## Quiz

Using the programming language of your choice, implement a simple quiz system using gRPC.  

### Specification

- The server streams a series of quiz questions to the client.
- The client answers each question one by one.
- The server checks each answer, updates the player’s total score, and returns that score immediately in the response.
- When there are no more questions, the server sends a final `RoundEnd` event to indicate that the round is finished.

### Protocol

The main RPCs are:

```proto
// Server to Client streaming RPC (questions)
rpc StreamQuestions(Join) returns (stream ServerEvent);

// Client to Server unary RPC (answers)
rpc SubmitAnswer(Answer) returns (Ack);
```

#### Messages

- **`Join`**  
  Sent by the client to start the question stream.  
  It includes the player identifier and game identifier:

  ```proto
  message Join {
    string player_id = 1;
    string game_id = 2;
    uint64 last_seen_seq = 3; // for resuming, or 0 to start fresh
  }
  ```

- **`ServerEvent`**  
  Used by the server to send different kinds of events over the same stream.

  ```proto
  message ServerEvent {
    uint64 seq = 1;
    oneof event {
      Question question = 2;
      RoundEnd round_end = 3;
    }
  }
  ```

  Each event can carry either a `Question` or a `RoundEnd`.

- **`Question`**  
  Represents a quiz question.

  ```proto
  message Question {
    string question_id = 1;
    string text = 2;
    repeated string choices = 3;
    int32 seconds_left = 4;
  }
  ```

  The `choices` field lists all possible answers, and `seconds_left` is informational.

- **`Answer`**  
  Sent by the client when answering a question.

  ```proto
  message Answer {
    string player_id = 1;
    string game_id = 2;
    string question_id = 3;
    string answer_id = 4;  // unique per answer (for idempotency)
    int32 choice_idx = 5;  // index in the list of choices
  }
  ```

- **`Ack`**  
  Returned by the server after receiving an answer.

  ```proto
  message Ack {
    bool accepted = 1;
    string reason = 2;
    int32 total = 3; // current score after the acknowledged answer
  }
  ```

  The `total` field shows the player’s current score, updated in real time.

- **`RoundEnd`**  
  Sent by the server at the end of the quiz.

  ```proto
  message RoundEnd {}
  ```

### Behaviour

1. The client starts by calling `StreamQuestions()` and receiving a stream of `ServerEvent` messages  
2. For each question received:  
   - The client displays the question text and choices  
   - The user selects a choice (by index)  
   - The client sends the answer via `SubmitAnswer()`  
   - The server checks whether the answer is correct and returns an `Ack` containing the updated total score  
3. When the server finishes sending questions, it sends a final `RoundEnd` event and closes the stream  
4. The client stops listening when the stream ends

### Steps

1. Create the `.proto` file defining:
   - The `Quiz` service with both RPCs (`StreamQuestions`, `SubmitAnswer`)
   - The required messages (`Join`, `ServerEvent`, `Question`, `Answer`, `Ack`, and `RoundEnd`)
2. Generate the gRPC stubs for your chosen language
3. Implement the server:
   - Load questions, choices, and correct answers from the local JSON file [`questions.json`](https://github.com/arturomorarioja-ek/SD_System_Integration_F26_Materials/blob/main/gRPC/questions.json)
   - Stream the questions to each client in order
   - For each submitted answer, check correctness and return an updated score in the `Ack`
4. Implement the client:
   - Call `StreamQuestions()` and display each incoming question
   - Prompt the user for an answer and send it with `SubmitAnswer()`
   - After each answer, display the updated score from the server
   - Stop when a `RoundEnd` event is received

### Expected result

- Each player sees questions appear in order  
- After answering each question, the client immediately shows the current total score  
- When the quiz ends, the client receives a `RoundEnd` event and exits gracefully

### Solution
[Python](https://github.com/arturomorarioja/py_grpc_quiz)

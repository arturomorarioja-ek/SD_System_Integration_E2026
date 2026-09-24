### Countries
Create the following queries in Trevor Blades's [Countries GraphQL API](https://countries.trevorblades.com/):

1. Retrieve the code and name of all continents

  ```graphql
  query {
    continents {
      code
      name
    } 
  }
  ```

2. For the continent with the code `EU`, retrieve the name, capital, and currency of all its countries

  ```graphql
  query {
    continent(code: "EU") {
      name
      countries {
        name
        capital
        currency
      }
    } 
  }
  ```

3. Add to the previous query the list of languages spoken in each country, including their name in English, their name in the language they give name to, and whether they are written from right to left

  ```graphql
  query {
    continent(code: "EU") {
      name
      countries {
        name
        capital
        currency
        languages {
          name
          native
          rtl
        }
      }
    } 
  }
  ```

4. For the language with the code `en`, retrieve the countries where it is spoken and the continent each country belongs to

  ```graphql
  query {
  	language(code: "en") {
      countries {
        name
        continent {
          name
        }
      }
    }
  }
  ```

5. Repeat the previous query so that it receives the country code as a parameter

  ```graphql
  query GetCountriesByLanguage($countryCode: ID!) {
  	language(code: $countryCode) {
      countries {
        name
        continent {
          name
        }
      }
    }
  }
  ```

6. Retrieve the name and capital of all countries. The query should receive a boolean parameter `$showLanguages` which, if true, should also include the code and name of all languages spoken in each country

  ```graphql
  query GetCountries($showLanguages: Boolean!) {
    countries {
      name
      capital
      languages @include(if: $showLanguages) {
        code
        name
      }
    }
  }
  ```

7. Update the previous query so that it filters countries by continent based on a parameter

  ```graphql
  query GetCountries(
    $continentCode: String!
    $showLanguages: Boolean!
  ) {
    countries(filter: { continent: { eq: $continentCode } }) {
      name
      capital
      languages @include(if: $showLanguages) {
        code
        name
      }
    }
  }
  ```

8. A company wants to list primary market countries (those in a specific continent that use a specific currency) and secondary markets (those in the rest of continents that use that specific currency). For each country, the following attributes will be shown: code, name, capital, and continent name. Write a query to solve this problem using a fragment

  ```graphql
  query MarketsByCurrencyAndContinent(
    $continentCode: String!
    $currency: String!
  ) {
    primaryMarkets: countries(
      filter: {
        continent: { eq: $continentCode }
        currency: { eq: $currency }
      }
    ) {
      ...CountryMarketInfo
    }
  
    secondaryMarkets: countries(
      filter: {
        continent: { ne: $continentCode }
        currency: { eq: $currency }
      }
    ) {
      ...CountryMarketInfo
    }
  }
  
  fragment CountryMarketInfo on Country {
    code
    name
    capital
    continent {
      name
    }
  }  
  ```

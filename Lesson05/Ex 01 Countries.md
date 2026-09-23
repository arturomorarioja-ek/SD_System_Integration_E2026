### Countries
Create the following queries in Trevor Blades's [Countries GraphQL API](https://countries.trevorblades.com/):

1. Retrieve the code and name of all continents

2. For the continent with the code `EU`, retrieve the name, capital, and currency of all its countries

3. Add to the previous query the list of languages spoken in each country, including their name in English, their name in the language they give name to, and whether they are written from right to left

4. For the language with the code `en`, retrieve the countries where it is spoken and the continent each country belongs to

5. Repeat the previous query so that it receives the country code as a parameter

6. Retrieve the name and capital of all countries. The query should receive a boolean parameter `$showLanguages` which, if true, should also include the code and name of all languages spoken in each country

7. Update the previous query so that it filters countries by continent based on a parameter

8. A company wants to list primary market countries (those in a specific continent that use a specific currency) and secondary markets (those in the rest of continents that use that specific currency). For each country, the following attributes will be shown: code, name, capital, and continent name. Write a query to solve this problem using a fragment

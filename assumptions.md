# Assumptions Doc

Add any and all assumptions that you made here!

Feel free to also use this space to document your thought process.

Design structure of Backend and DB:
- Database model: Hybrid, so fetches from external endpoint and MongoDB(NoSQL DB so easier to fetch and less mapping issues)
- System that will implement/code API - using Spring framework
  - Spring Boot allows us to quickly bootstrap our application
  - Maven build system allows us to add dependencies and not have to worry about downloading external files
  - Maven also allows us to package this backend system into a JAR file


Connection from Spring Boot application to MongoDB:
- Provide specific dependencies in pom.xml file
- Configured in application.properties
- We can use Repository Interface that is a subclass of MongoDB repository to help us with Object Relational Mapping(ORM)
   - This repository will have CRUD functionalities: Create, Remove, Update, Delete(We will not need Update here though)

API Setup:

Tracking system = List<Recipe> we will use to keep track of tracked recipes, and we will remove them from the List when necessary to "untrack" them
- GET endpoint
   - Assumption: Return recipes from MongoDB
   - Path variables: city
   - External API call - https://kcbrjk8zn4.execute-api.us-west-1.amazonaws.com/eat-food-uwu with API key, city and previous parameters
   - ONLY NEED TO RETURN EACH RECIPE'S ID!
   - Only return those recipes that are not in the List<Recipe>

- POST endpoint
   - We will be using our repository to add new entries to our MongoDB DB
   - We will need to have this database store all the recipes from external API call
   - If we POST a recipe, but it is contained in the List<Recipe>, then 

- DELETE endpoint
   - If a recipe in our MongoDB needs to be deleted, delete it
   - If a record from existing in external DB needs to be deleted, we keep track of it in a List<Recipe> and don't return them


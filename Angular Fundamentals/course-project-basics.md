# Planning the App

- planning general structure of the app
  -root component will be responsible to hold other component
  other features can be have its own component
- header component for its navigation between recipe and shoppinglist

Ientify the features
component for the features
model - the data to be used in the component

ng new course-project --no-strict
npm install --save bootstrap@3
ng g c recipes --skip-tests true
ng g c recipes/recipe-list --skip-tests true

same component, same structure to be refferred throughout the Recipe project, so we create a model for it.
model is a typescript file

**Model** is just a blue print of objects that we create and typescript class does this job. A class can be instantiate new objects based on the setup provided in model.

\<img
src="{{ recipe.imagePath }}"
[src]=" recipe.imagePath "
alt="{{ recipe.name }}"
class="img-responsive"
style="max-height: 50px"
/>

shared folder contains features or elements needed to be shared across different component

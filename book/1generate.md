## Generate Angular App

1. Generate the app using Angular CLI by running

   ```sh
ng new <name of app>
   ```
   When prompted, select the following options:
   - Select **YES** to include routing
   - Select SCSS (or Sass) for styles

   ![](assets/emojis/boom.png) You used your first schematic of the workshop.

1. Open the new app in your IDE and serve the app using `ng serve --o` as a refresher of what you get out of the box.

1. Stop serving the app. The next step changes _angular.json_ and the watcher won't catch changes made in that file.

1. Let's get Angular Material library in here. The Material library houses a collection of UI components that use Material design specifications. Use Angular CLI's `add` command to run the schematic created by the Material team.

   ```sh
ng add @angular/material
   ```
   When prompted, select the following options:
   - Select your theme color (pick anything except **Custom**)
   - Include `hammerjs` 
   - Include browser animations

1. A lot happened in this schematic. Here's some of the changes made to your app 
   - added npm packages
   - added Angular's **CDK** **C**omponent **D**evelopment **K**it library, a dependency for Angular Material
   - updated the _angular.json_ file to include your theme 
   - imported `hammerjs` to your main entry files for both the app and for testing 
   - added browser animations
   - imported Material icons
   - added some default styles 

   You can read up more about what all happened in [Material's Schematic Guide](https://material.angular.io/guide/schematics).

   {% hint style="info" %}
Material is an opinionated library. If you don't want all the opinions, you can use the CDK instead (but doesn't have as many control options) or back out some of the style changes.
   {% endhint %}

1. Start your app again for the remainder of the workshop.


{% hint style="tip" %}
[See the results on StackBlitz](https://stackblitz.com/github/angularkc/schematics-workshop-worksheet/tree/master/examples/1generate)
{% endhint %}
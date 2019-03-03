# Navigation View

We'll create a navigation view for the app using Material's built in schematic to quickly scaffold out a responsive nav list. This schematic is different from the ones we used before-- we'll use CLI's `generate` command. In addition to generating components or services, the `generate` command takes a schematic as a param to generate code so that anyone can create and distribute their own schematic. 

1. Generate the nav view by running the following command. You can pass in any name for the component. We'll call it 'navigation' for simplicity.

   ```sh
ng generate @angular/material:nav <component-name>
   ```

   {% hint style="info" %}
The schematic creates a component and adds it to the `AppModule` like what you'd expect if you created a component without using a schematic. It also imports Material control dependencies and adds a lot more code to the component than a basic component generation.
   {% endhint %}

   {% hint style="danger" %}
If your component styles generated as CSS instead of SCSS, you'll need to rename the file to _*.scss_ and update the link in the _*.component.ts_.
   {% endhint %}

1. To consume this new component, replace all the code in _app.component.html_ with the selector for the nav component.
  
   {% hint style="working" %}
Delete the generated code in the _app.component.html_ and add `<app-navigation></app-navigation>`.
   {% endhint %}

1. View your reloaded app. ![](assets/emojis/party-popper.png)

1. Resize your browser window or use your browser's device emulation mode to see how the nav list changes for smaller form factors.

1. Take a peek at the code for the navigation component. In particular, check out the _component.ts_ and the _component.html_.
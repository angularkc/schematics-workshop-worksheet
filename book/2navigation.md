# Navigation View

We'll create a navigation view for the app using Material's built in schematic to quickly scaffold out a responsive nav list. This schematic is different from the ones we used before-- we'll use CLI's `generate` command. In addition to generating components or services, the `generate` command takes another named schematic as a parameter to generate code so that anyone can create and distribute their own schematic. 

1. Generate the navigation view by running the following command. You can pass in any name for the component. We'll call it 'navigation' for simplicity.

   ```sh
ng generate @angular/material:nav <your-component-name OR navigation>
   ```

   {% hint style="info" %}
The @angular/material:nav schematic creates a component and adds it to the `AppModule` like what you'd expect if you created a component without using a schematic. It also imports Material ui control dependencies and adds code to the component to create a navigation menu.
   {% endhint %}

   {% hint style="danger" %}
If your component styles generated as CSS instead of SCSS, you'll need to rename the file to _*.scss_ and update the `stylesUrl` link in the _*.component.ts_.
   {% endhint %}

1. To consume this new component, replace all the code in _app.component.html_ with the selector for the nav component.
  
   {% hint style="working" %}
Delete the generated code in the _app.component.html_. If you used the name `navigation` for the component name add `<app-navigation></app-navigation>`, otherwise use the name of your component.
   {% endhint %}

1. View your reloaded app. ![](assets/emojis/party-popper.png)

1. Take a peek at the code for the navigation component. In particular, check out the _navigation.component.ts_ and the _navigation.component.html_. Notice the template stubs in a menu list. We'll update that soon.

   {% hint style="danger" %}
The @angular/material:nav schematic contains a small bug in version 8.1.3. If all you see is a toolbar, then we need to make a small change in the template to display the side navigation menu. In _navigation.component.html_ find the property binding for the `[opened]` attribute. We want the `mat-sidenav` element to open when the `isHandset$` property is false. Change the property binding to `[opened]="!(isHandset$ | async)"`. 
   {% endhint %}

1. Resize your browser window or use your browser's device emulation mode to see how the nav menu changes for smaller form factors.

{% hint style="tip" %}
[See the results on StackBlitz](https://stackblitz.com/github/angularkc/schematics-workshop-worksheet/tree/master/examples/2navigation)
{% endhint %}

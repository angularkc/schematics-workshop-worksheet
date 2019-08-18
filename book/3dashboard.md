# Dashboard

Material has a few more schematics we can play with. Let's create a dashboard view as the main view for this app. This schematic uses cards arranged in a grid list.

1. Generate the dashboard view by running the following command. You can pass in any name for the component. We'll use 'dashboard' for simplicity.

   ```sh
ng generate @angular/material:dashboard <your-component-name OR dashboard>
   ```

1. To consume this new component, find the comment "Add Content Here" in _navigation.component.html_. Replace the comment with the dashboard component selector.

1. View your reloaded app. ![](assets/emojis/party-popper.png)

1. Resize your browser window or use your browser's device emulation mode to see how the cards in nav list changes for smaller form factors.

1. Take a peek at the dashboard component code. Feel free to change card titles or sizes.

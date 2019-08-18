# To Do List

Now let's add a todo list and use one of the newest features from the Material team, drag and drop. This schematic resides in the CDK library.

1. Generate the todo list by running the following command. You can pass in any name for the component. We'll use 'todo' for simplicity.

   ```sh
ng generate @angular/cdk:drag-drop <your-component-name OR todo>
   ```

1. Since we'll want to see both the dashboard and the todo via the nav list, we'll need to set up routing. Add routes for the dashboard and todo views in _app-routing.module.ts_. You'll have something similar to this depending on your component names.

   {% filename %}app-routing.module.ts{% endfilename %}
   ```ts
const routes: Routes = [
  { path: 'dashboard', component: DashboardComponent },
  { path: 'todo', component: TodoComponent },
  { path: '', redirectTo: '/dashboard', pathMatch: 'full' },
  { path: '**', component: DashboardComponent }
];
   ```

1. In _navigation.component.html_, make the following changes we now want to consume the router outlet. Replace the component selector for your dashboard component (if you used the same names we did, that's `<app-dashboard></app-dashboard>`) with `<router-outlet></router-outlet>`.

1. We want to build a nav menu, so first let's update the text for each anchor element in the order we want to see the menu items. First we want dashboard as the main initial view, followed by the todo list. Update the text in the first two anchor elements to "Dashboard" and "Todo".

1. The @angular/material:nav schematic automatically adds `href` attributes to the anchor tags. Since we want to use the router, replace the `href` with `routerLink` for both "Dashboard" and "Todo".

1. We need to set the `routerLink` value. The value should match the route you defined in _app-routing.module.ts_ (plus a slash in front) for the component. For dashboard, use the value `/dashboard`. Repeat for "Todo" anchor element. Your "Dashboard" anchor element will look like this:
   
   {% filename %}navigation.component.html{% endfilename %}
   ```html
   <a mat-list-item routerLink="/dashboard">Dashboard</a>
   ```

1. Now when you click on a link the view changes between the dashboard and your todo list! But we want to make it easy to see which link we're on by changing the color of the link when it's in view. Add the `routerLinkActive="active"` directive and value to the dashboard and todo anchor tags. This will use a class we'll create named `.active` whenenver the router link associated to that view is active.

1. In _navigation.component.scss_, add a class for `.mat-list-item.active` to set the background color. You can pick any color of your choosing or we can set it to the complementary (accent) color of your material theme by importing the theming file and using the complementary color (shown in the code snippet below).

   Your navigation component code will look like this
    {% codetabs name="navigation.component.html", type="html" -%} 
<mat-sidenav-container class="sidenav-container">
  <mat-sidenav #drawer class="sidenav" fixedInViewport="true"
      [attr.role]="(isHandset$ | async) ? 'dialog' : 'navigation'"
      [mode]="(isHandset$ | async) ? 'over' : 'side'"
      [opened]="!(isHandset$ | async)">
    <mat-toolbar>Menu</mat-toolbar>
    <mat-nav-list>
      <a mat-list-item routerLink="/dashboard" routerLinkActive="active">Dashboard</a>
      <a mat-list-item routerLink="/todo" routerLinkActive="active">Todo</a>
      <a mat-list-item href="#">Link 3</a>
    </mat-nav-list>
  </mat-sidenav>
  <mat-sidenav-content>
    <mat-toolbar color="primary">
      <button
        type="button"
        aria-label="Toggle sidenav"
        mat-icon-button
        (click)="drawer.toggle()"
        *ngIf="isHandset$ | async">
        <mat-icon aria-label="Side nav toggle icon">menu</mat-icon>
      </button>
      <span>schematics-workshop</span>
    </mat-toolbar>
    <router-outlet></router-outlet>
  </mat-sidenav-content>
</mat-sidenav-container>
    {%- language name="navigation.component.scss", type="css" -%} 
@import '~@angular/material/theming';

.sidenav-container {
  height: 100%;
}

.sidenav {
  width: 200px;
}

.sidenav .mat-toolbar {
  background: inherit;
}

.mat-toolbar.mat-primary {
  position: sticky;
  top: 0;
  z-index: 1;
}

.mat-list-item.active {
  background: mat-color($mat-pink, 500);
  color: mat-contrast($mat-pink, 500);
}
    {%- endcodetabs %}

   {% hint style="tip" %}
Please let us know if you're interested in hearing about theming Material, using Material components, or using the CDK in future AngularKC meetups. We're always looking for topic suggestions. We also want to hear about your projects and new-to-you technologies so feel free to let us know if you want to share/present something at a future meetup. 
   {% endhint %}

1. View your reloaded app. ![](assets/emojis/party-popper.png)

1. Resize your browser window or use your browser's device emulation mode to see how the todo list changes for smaller form factors.

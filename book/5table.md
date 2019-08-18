# Table

For our last schematic, we'll add a table that has pagination and sorting built in.

1. Generate the table by running the following command. You can pass in any name for the component. We'll use 'table' for simplicity.

   ```sh
ng generate @angular/material:table <your-component-name OR table>
   ```

1. We'll add table as the 3rd item in our nav list. Make the following changes like we did for dashboard and todo components on the previous page
   - Add table route to the _app-routing.module.ts_
   - Update the router links and link name in _navigation.component.html_ 

1. The table view is full width and is a little hard to see what's going on so let's add a little space to the view. In _table.component.html_ find the top level `div` and add a class named 'table-container'. In _table.component.scss_, create a style for the class and set 'margin: 50px'.

   {% codetabs name="table.component.html", type="html" -%} 
<div class="mat-elevation-z8 table-container">
  <table mat-table class="full-width-table" [dataSource]="dataSource" matSort aria-label="Elements">
    ...

    <tr mat-header-row *matHeaderRowDef="displayedColumns"></tr>
    <tr mat-row *matRowDef="let row; columns: displayedColumns;"></tr>
  </table>

  <mat-paginator #paginator
      [length]="dataSource.data.length"
      [pageIndex]="0"
      [pageSize]="50"
      [pageSizeOptions]="[25, 50, 100, 250]">
  </mat-paginator>
</div>
   {%- language name="table.component.scss", type="css" -%} 
.table-container {
  margin: 50px;
}

.full-width-table {
  width: 100%;
}
    {%- endcodetabs %}


1. Your app is complete!

   ![](https://media.giphy.com/media/9Jcw5pUQlgQLe5NonJ/giphy.gif)


{% hint style="tip" %}
[See the results on StackBlitz](https://stackblitz.com/github/angularkc/schematics-workshop-worksheet/tree/master/examples/5table)
{% endhint %}

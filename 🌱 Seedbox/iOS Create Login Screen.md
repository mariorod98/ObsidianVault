up::
tags:: #state/seedling

# iOS Create Login Screen

1. Create a new project.
2. Remove the generated ViewController, as we will create a custom one.
3. Create a new ViewController in the Main storyboard (using the + button in the top right corner or with the comand CMD+Shift+L).
4. If we launch the app, it will show a black screen because we haven't defined the entry point of the story board.
5. To select the entry point, select the controller and in the inspector Check Is Initial View Controller.
6. Now we have to create the layout.
7. Create a new Stack View (+ button) and drop it in the Scene. The stack view size is determined by the size of its children, growing and shrinking to accomodate to their size.
8. Create a new Label and drop it in the Stack View.
9. Create a new TextField and drop it in the Stack View. Now the Stack View should have the size adjusted to its children.
10. Change the text of the label to Username.
11. Copy and paste both components to create the password elements and change the password label text.
12. To center the StackView, right click and drag to the View object. Select the leading and Subtrailing options, as well as Center Vertically. Now it is centered vertically
13. In the inspector of the StackView, we can change the constraint values, both horizontal and vertical constraints. Change the Leading and Trailing constraint so that its Constraint values are 20.
14. In the StackView Inspecctor we can add padding between its children modifying the property Spacing.

## References

---
Planted: 2023-01-19
Last tended: 2023-01-19
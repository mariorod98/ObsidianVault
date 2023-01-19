up::
tags:: #state/seedling

# iOS Create Login Screen
## Create and setup the project
1. Create a new project.
2. Remove the generated ViewController, as we will create a custom one.
3. Create a new ViewController in the Main storyboard (using the + button in the top right corner or with the comand CMD+Shift+L).
4. If we launch the app, it will show a black screen because we haven't defined the entry point of the story board.
5. To select the entry point, select the controller and in the inspector Check Is Initial View Controller.

## Create the layout
7. Create a new Stack View (+ button) and drop it in the Scene. The stack view size is determined by the size of its children, growing and shrinking to accomodate to their size.
8. Create a new Label and drop it in the Stack View.
9. Create a new TextField and drop it in the Stack View. Now the Stack View should have the size adjusted to its children.
10. Change the text of the label to Username.
11. Copy and paste both components to create the password elements and change the password label text.
12. To center the StackView, right click and drag to the View object. Select the leading and Subtrailing options, as well as Center Vertically. Now it is centered vertically
13. In the inspector of the StackView, we can change the constraint values, both horizontal and vertical constraints. Change the Leading and Trailing constraint so that its Constraint values are 20.
14. In the StackView Inspecctor we can add padding between its children modifying the property Spacing.
15. To add a background image, go to the assets folder and drag the image to the folder.
16. Create a new ImageView component and change the attribute Image to th
17. Connect the image constraints to the View and select Equal Width and Equal Heights, Center Horizontally and Center Vertically. OR we can specify that their top, bottom, leading and trailing constraints match the parent (setting the constraint value to 0).
18. If the image is at the front of the other elements, just rearrange the elements sending the image to the top of the view childs, just under the SafeArea child.
19. iPhone tries to maintain the aspect ratio of the image and keep all the image inside the Scene. If we want to fill all the space, croping the image, modify the property
20. The image is only visible inside the safe area, outside it is white. To fill all the screen, change the top and bottom constraint attributes "Second Item" to SuperView.

## References

---
Planted: 2023-01-19
Last tended: 2023-01-19
# Definitions
**Seams.** Similar to seams in a piece of clothing, they give you control of how the texture is applied in your mesh.
**Sharps.** Gives control of how hard and soft our angles are rendered.

# Modes
**Object mode**. The default mode. Can move, rotate and scale an object.
**Edit mode**. Modify geometry of the object.

# Shortcuts
## Most basic
tab: switch object/edit mode
### Move around
wheel button + move mouse : rotate camera
shift + wheel button + move mouse: move in 2D
ctrl + wheel button + move mouse: move in the third axis

 middle mouse up/down: zoom
CTRL + Shift + mouse up/down: zoom slowmo
. in numpad: zoom in selected

### Select views
numpad 1:  front
numpad 3: sideview
numpad 7: topview
ctrl + numpad 1: rear
ctrl + numpad 2: opposite side
ctrl + numpad 3: bottom

### Contextual menus
shift + Space:  open gizmo menu
shift + A : open primitives menu
shift + S: cursor menu
T : show/hide left-hand menu
N: show/hide menu side bar

ctrl + Space : clear every menu from viewport

## Object mode
### How to reset transforms
I have to look deeper into what this means but, when we are editing an object, it keeps the transform of the original object. If we then want to modify it through Modifiers, weird results can occur. Therefore we need to reset the transforms of the object so that they match its current shape, not the original one.

To open the reset menu press Ctrl + A and to reset the transforms press All Transforms.

Reset transformations will set the origin of the transformation to the origin of the world. To set them back to the center of the object, we must right click the object and Set Origin to Origin to Geometry

## Edit Mode
L : select the whole connected mesh that the mouse is pointing at. If the mesh has seams and we are in face mode, it respects the seams. This does not restarts your selection, it adds the mesh to what you have currently selected.
P: open separation menu to separate a group of faces from another mesh, creating a new mesh
alt + shift + click: quick select loop
Y: disconnects a selection of elements from the rest of the mesh WITHOUT creating a new object

### Face mode
i : insert faces

### Cut tool
Cut tool creates new edges.
To acces cut mode you have to be in Edit mode (and in vertex mod maybe).
Press K to open cut tool and select the vertex where you want to start the cut.
To make a straight cut, press A to fix the direction.

### How to cut a face evenly
In Edit mode, select a vertex of the face and press ctrl+R. Move the cursor to the closest edge to create a split from that edge to the opposite.  It will initially be set to the center of the edge but can be moved.

You can modify the number of edges created with the mouse wheel. They will be arranged evenly.

### How to fill holes
Go to menu Mesh->Clean up->Fill holes to fill all the wholes of the selection

### Select multiple elements in Edit Mode
If you want to select different especific elements, use shift + left click to select each element

If you want to select consecutive elements, select the first element and then ctrl + left click the last element and it will select all in between

## Marking seams
Seams are useful to divide a mesh into subparts and work only in that subpart so that you don´t have to select all the especific **faces** all the time. Seams only work with faces.

## Others
right click: if making a change to an object, cancel the change
a: select all
shift + d: duplicate mesh
g: move object freely
\[r,s] + \[x,y,z]: rotate/scale on that axis
\[r,s] + \[x,y,z] + num: rotate/scale on that axis by that value
shift + right click: set cursor positiom


ctrl + shift + b: bevel vertices
ctrl + R: create edgeloop

e: extrude
l: select all connected meshes
p (edit mode) : separate mesh menu
ctrl + a: reset transform
i: insert 
h: hide selected
shift + h: hide everything but selected

## Modifier window
ctrl + a: apply modifier

# Modifiers
Ctrl + A: apply a modifier

## Solidify
Makes a surface thick

## Troubleshoot
## I have marked seems in my edges and separated a piece of the mesh from the rest but when moving it, the rest of the mesh follows.
Solution: You have the smoothing activated. **Deactivate it.**
![[Pasted image 20240620213352.png]]
# Definitions
**Seams.** Similar to seams in a piece of clothing, they give you control of how the texture is applied in your mesh.
**Sharps.** Gives control of how hard and soft our angles are rendered.
# Modes
**Object mode**. The default mode. Can move, rotate and scale an object.
**Edit mode**. Modify geometry of the object.

# Shortcuts
## Move around
wheel button + move mouse : rotate camera
shift + wheel button + move mouse: move in 2D
ctrl + wheel button + move mouse: move in the third axis

 middle mouse up/down: zoom
CTRL + Shift + mouse up/down: zoom slowmo
. in numpad: zoom in selected

## Select views
numpad 1:  front
numpad 3: sideview
numpad 7: topview
ctrl + numpad 1: rear
ctrl + numpad 2: opposite side
ctrl + numpad 3: bottom

## Contextual menus
shift + Space:  open gizmo menu
shift + A : open primitives menu
shift + S: cursor menu
T : show/hide left-hand menu
N: show/hide menu side bar

ctrl + Space : clear every menu from viewport

## Cut tool
Cut tool creates new edges.
To acces cut mode you have to be in Edit mode (and in vertex mod maybe).
Press K to open cut tool and select the vertex where you want to start the cut.
To make a straight cut, press A to fix the direction.

## How to cut a face by half
In Edit mode, select a vertex of the face and press ctrl+R. Move the cursor to the closest edge to create a split from that edge to the opposite.  It will initially be set to the center of the edge but can be moved

## Select multiple elements in Edit Mode
If you want to select different especific elements, use shift + left click to select each element

If you want to select consecutive elements, select the first element and then ctrl + left click the last element and it will select all in between
## Others
right click: if making a change to an object, cancel the change
a: select all
shift + d: duplicate mesh
g: move object freely
\[r,s] + \[x,y,z]: rotate/scale on that axis
\[r,s] + \[x,y,z] + num: rotate/scale on that axis by that value
shift + right click: set cursor position





tab: switch object/edit mode


ctrl + shift + b: bevel vertices
K: enter cutting mode
a (while in cutting mode) : fix to the z axis
ctrl + R: create edgeloop

alt + shift + click: quick selection loop
e: extrude
l: select all connected meshes
p (edit mode) : separate mesh menu
ctrl + a: reset transform
i: insert 

h: hide selected
shift + h: hide everything but selected

## Modifier window
ctrl + a: apply modifier
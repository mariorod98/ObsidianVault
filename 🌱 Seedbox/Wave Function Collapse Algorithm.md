up:
tags: #state/seedling

# Wave Function Collapse Algorithm
The Wave Function Collapse (WFC) is an algorithm that generates procedural images. It uses constraint solving to generate an output image based on an example image or a set of rules. 

The WFC can be extended to use tilesets to generate tilemaps and even 3D blocks to generate a 3D environment. 

## Simple explanation
The WFC algorithm uses a structure, called **wave**, to handle all the possibilities for each node (or position) in the output image. This **wave** stores the candidate tiles of each position.

![[WFC_wave.png | 300]]
Image 1. The state of the **wave** in a specific iteration of the algorithm.

The algorithm can be broken down into two phases:
- **Observation phase**. Here the algorithm chooses the a position of the image (based on its *entropy*) and **collapses** that position. This means that it chooses a tile from the candidates in the **wave**, eliminating the rest of the candidates for that node.
- **Propagation phase**. Once a candidate has been chosen, it must propagate the decision to the rest of the nodes of the image. This propagation works by adjacency. The algorithm will check the neighbors of the current tile to see if any candidate must be removed. If a candidate of a neighbor is removed, then its neighbors must be checked too. The propagation stops when all the changes have been checked.

## Initial State
To start the algorithm, the following input must be handed:
- **tileset**. The set of tiles that the algorithm will be working with.
- **weights**. A set of weights, with each weight corresponding to the weight of a tile in the tileset.
- **rules**. A set of adjacency rules that defines which tiles can be put next to one another.
- The number of **rows** and **columns** of the output image.

In the initialization of the algorithm, the following structures must be created and initialized:
- **wave**. This structure stores, for each node in the image, the available candidate tiles that can be placed in that position. Its size is **rows** x **columns**.
- **entropy**. A list that stores the entropy value of each node of the output image.

## Observation phase


## References
[GitHub - mxgmn/WaveFunctionCollapse: Bitmap & tilemap generation from a single example with the help of ideas from quantum mechanics](https://github.com/mxgmn/WaveFunctionCollapse)

[Superpositions, Sudoku, the Wave Function Collapse algorithm. - YouTube](https://www.youtube.com/watch?v=2SuvO4Gi7uY&ab_channel=MartinDonald)

[The Wavefunction Collapse Algorithm explained very clearly | Robert Heaton](https://robertheaton.com/2018/12/17/wavefunction-collapse-algorithm/)

[Modifying Wave Function Collapse for more Complex Use in Game Generation and Design](https://digitalcommons.trinity.edu/cgi/viewcontent.cgi?article=1058&context=compsci_honors#:~:text=Wave%20Function%20Collapse%20(WFC)%20is,a%20similar%2C%20yet%20novel%20output.)

[Wave Function Collapse Explained – BorisTheBrave.Com](https://www.boristhebrave.com/2020/04/13/wave-function-collapse-explained/)

[Wave - by Oskar Stålberg](https://oskarstalberg.com/game/wave/wave.html)

[SGC21- Oskar Stålberg - Beyond Townscapers - YouTube](https://www.youtube.com/watch?v=Uxeo9c-PX-w&t=420s&ab_channel=SwedenGameArena)

[Phantom Brigade - Mech, Turn-Based, Tactical RPG](https://forums.tigsource.com/index.php?topic=54424.0)

[Why I'm Using Wave Function Collapse for Procedural Terrain | Unity Devlog - YouTube](https://www.youtube.com/watch?v=20KHNA9jTsE&ab_channel=DVGen)

[Wave Function Collapse tips and tricks – BorisTheBrave.Com](https://www.boristhebrave.com/2020/02/08/wave-function-collapse-tips-and-tricks/)

[EPC2018 - Oskar Stalberg - Wave Function Collapse in Bad North - YouTube](https://www.youtube.com/watch?v=0bcZb-SsnrA&ab_channel=BUasGames)

---
Planted: 2022-05-13
Last tended: 2022-12-24
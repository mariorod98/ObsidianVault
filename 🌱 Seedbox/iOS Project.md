up::
tags:: #state/seedling

# iOS Project
user: pvesat
password: esata123456*

## Create a project
Ideally, the Product Name should be all in lower caps.

## Elements
- Main scene. Pantalla inicial de la aplicación creada por defecto.
- LaunchScreen scene. Pantalla de carga que sale antes del Main por defecto.

## Targets
El target tiene 

## ViewController
It is similar to the Android Activity both in lifecycle and in function.

## Scene
A scene is similar to a layout in Android. It is assigned to a specific controller. The controller it is assigned to can be modified in its properties in `CustomClass->Class`.

If a scene has an entry point, then the app can be launched through that scene.

## App delegate
The app delegate is the root object of the appm that manages its behaviour.
The app delegate handles when the app is resumed, paused, etc.
It also handles deep links (similar to intents in Android).
## How to bind a scene element to a ViewController
1. Divide Xcode in two panels to have the view and the controller sied to sied
2. Select the element and drag to the position in the code where you want to create the variable
3. Give a name to the variable. It must be follow the syntax: nameType.


If a button is connected, depending of the place it is connected, a new variable will be created OR an event for the button
## Swift

The exclamation symbol `!` specifies that a variable must exists always
`weak var helloLabel: UILabel!` 
## References

---
Planted: 2023-01-12
Last tended: 2023-01-12
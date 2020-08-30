Swift always uses "Model View Controller", a way to divide objects in the system.

- One MVC typically only controls only one screen. 
- Apps have tons of screen. An app would be made of many MVC.
- ![Screen Shot 2020-07-10 at 5.49.20 PM](/Users/trxn/Library/Application Support/typora-user-images/Screen Shot 2020-07-10 at 5.49.20 PM.png)
- Other MVCs may be treated as views to a MVC; they communicate blindly. Notice that the arrows are minimal.

*Model* is a UI independent set of object that is the *"what"* of the the app. (The part of the app that knows how to play the Concentration game.)

*Controller* is the *"how"* your Model is displayed on the screen; the UI logic.

*View* is the Controller's minions. Generic UI elements (button, view controller, label) that the controller has to communicate with the model to get the game onto the UI.

Communication:

![Screen Shot 2020-07-10 at 5.48.48 PM](/Users/trxn/Library/Application Support/typora-user-images/Screen Shot 2020-07-10 at 5.48.48 PM.png)

- Controller always talks directly to the Model and the View (*outlet* to the flipCount label). 
- Model and the View should never speak to each other.
  - View are buttons. How could buttons know what the app is about. 
- View should talk "blindly" and be structured when talking to the Controller. (target actions)
  - Everytime a button, from View is pressed, it calls a *target*, which is part of the Controller. The View is sending an *action* when things happen.
  - Views may need to synchronize with the Controller (scroll view). Then, the Controller sets itself as the View's *delegate* (`should`, `will`, `did`). 
    - Delegates are set via a protocol.
  - View do not own the data they display; not part of its instance variables. (can't possible display 50,000 music items). Controllers almost always act as a *data source* (`data at`, `count`).

- Controllers interpret/format Model information for the View
- Model uses a "radio station"- like mechanism to update the controller called *notivication or K&O*. Controllers or other Model will "tune in" to changes. 
  - A View may "tune in", but to a controller radio station.
## Model View ViewModel
### Software design pattern which separates application into three components:
- #### Model - manages app data, contains business logic
- #### View - [[UI]], displays data it gets from ViewModel, does NOT interacts with Model directly (only through ViewModel)
- #### ViewModel - a layer between Model and View, convert Model's data from its format to a format that is suitable for View to display
### [[MVVM.canvas|MVVM Schematic]]
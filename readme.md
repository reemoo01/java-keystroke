# Project Genome

----------


Project Genome is a simple Keystroke Biometrics Capture Software. It captures the exact time when a key on the keyboard is pushed up or down and uses that data to derive variables such as Duration, Seek, and Latency.

## What is Keystroke Biometrics






From Wikipedia 
	

> Keystroke dynamics, keystroke biometrics, typing dynamics and lately typing biometrics, is the detailed timing information which describes
> exactly when each key was pressed and when it was released as a person
> is typing at a computer keyboard.

Essentially, this project is a part of an experiment to see if one's typing habits can be used to identify them in an authentication setting. This works by capturing three variables.

 - **Duration** - The time it takes for a single key to be pushed up and released
 - **Seek** - The time it takes to switch from one key to the next
 - **Latency** - The time it takes from pressing/releasing a key to pressing/releasing the next key.

![A description of variables that are captured in keystroke biometrics.](https://raw.githubusercontent.com/AKil47/Genome/master/Variables.png)

# Getting Started



The Java Program follows can be executed from source by running

    javac Main.java

This will execute the programs main function which will render the JavaFX Stage from the UI.fxml file and initialize the program's objects. Below shows an explanation of the code's logic.

# Program Logic

The program is structured with a variety of different objects and packages for ease of understanding. These objects are detailed below:

### The `Capture` Package
The capture package contains the `capture.fxml` and `CaptureController.java` files
These files simply outline the UI and the event handlers that actually capture the typing data. The data is automatically appended to an auto-generated csv file.

### The `Analyze` Package
This package contains a large amount of classes that are used to sort and extract data points from the data captured from the `Capture` Package. 

The UI is defined by an `analyze.fxml` and an `Analyze Controller.java`. The controller simply initializes the other `Analyze` objects and creates event handlers.

#### Interacting with Files
The `fileImporter` class and the `fileExporter` class import and export csv files respectively. 

The `fileImporter` class imports the csv into three `ArrayLists` using a simple `Scanner` object. This convention of using `ArrayLists` to store and manipulate the data is implemented throughout the program.

The `fileExporter` class simple prints data generated from the `Sorter` and `varExtractor` classes. It prints in in such a way that the csv file can be opened in Microsoft Excel or any other csv view for ease of access. It does this via for loops that help traverse the data generated by the `varExtractor` and `Sorter`.

#### The Analysis Functions
The `analyze` package contains two important classes:

 1. `Sorter.java`
 2. `varExtractor.java`

These can be used to parse and extract data from csv files generated from the `capture` package.

The Sorter Works as Follows:

> 1.The `Sorter` takes input from `fileInput` in the form of three `ArrayLists`
> as mentioned earlier.
>  2. The `Sorter` then traverses the `ArrayList` in search for the first "DOWN"
>  3. The `Sorter` then traverses the `ArrayList` from the "DOWN" point in search of the first matching "UP"
>  4. The two letters are found and `returned`.

The `varExtractor` Works as Follows

> 1. The `varExtractor` gets information from the `Sorter` in the form of three `ArrayLists`
> 2. The `varExtractor` utilizes a variety for `loops` for each respective method for each variable
> 3. The data is returned in the form of three columns for usage by the `Exporter`.




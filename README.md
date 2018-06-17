# CreateML: Tomato Banana

This is a minimal example to show you how CreateML works. We will create a CoreML model that is able to detect bananas and tomatoes.

# Training Data
First, we need data to train the model with. CreateML makes labeling very easy: Create a new folder for your images. In this folder, create two new folders: one named `banana`, the other one named `tomato`. Now download a bunch of images from the internet (search for "banana" or "tomato") and put them into their according folders. The result should look like this:

![Folder](https://raw.githubusercontent.com/frogg/CreateML-Tomato-Banana/master/screenshots/training%20data.png)

# Setup Xcode Playground
Now, got to Xcode and select `File` —> `New` —> `Playground` —> `macOS` —> `blank`.

# Code
To show the CreateML drag and drop user interface we need to write some very minimal code:
```Swift
import CreateMLUI

let builder = MLImageClassifierBuilder()
builder.showInLiveView()
```

This imports the framework and generates the user interface (`.showInLiveView`).

Now, run your code!

# Training
A new UI should appear in the assistant editor / live view. You can now drag the `image` folder from earlier into this UI – CreateML will start training with your data immediately. 
After a few seconds the process is complete and you can see the results in the console:
![result](https://raw.githubusercontent.com/frogg/CreateML-Tomato-Banana/master/screenshots/xcode%20playground.png)
```
+------------------+--------------+------------------+
| Images Processed | Elapsed Time | Percent Complete |
+------------------+--------------+------------------+
| 1                | 7.64s        | 5.75%            |
| 2                | 7.69s        | 11.75%           |
| 3                | 7.74s        | 17.5%            |
| 4                | 7.79s        | 23.5%            |
| 5                | 7.83s        | 29.25%           |
| 10               | 8.19s        | 58.75%           |
| 17               | 8.48s        | 100%             |
+------------------+--------------+------------------+
Skipping automatic creation of validation set; training set has fewer than 50 points.
Beginning model training on processed features. 
Calibrating solver; this may take some time.
+-----------+--------------+-------------------+
| Iteration | Elapsed Time | Training-accuracy |
+-----------+--------------+-------------------+
| 1         | 0.033924     | 1.000000          |
+-----------+--------------+-------------------+
SUCCESS: Optimal solution found.
Trained model successfully saved at /var/folders/77/d8w7sf5n1wxd9g33wtjq9wy40000gn/T//ImageClassifier.mlmodel.

```

# Executing and Testing the Model
To see how well the model performs we can test it with some images that it has never seen before. This is important to verify that the model is not overfitted on our training data!

Just download some more banana and tomato images and drag them onto the model:
![testing](https://raw.githubusercontent.com/frogg/CreateML-Tomato-Banana/master/screenshots/testing.png)

As you can see, both bananas and tomatoes are classified correctly…yaayy!

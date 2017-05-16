# Creating Datasets...

In this tutorial, we will explain you how to create divers Datasets from multiple types and multiple dimensions.
The Dataset class is an Abstract class, because of that, it's impossible to create a Dataset like that:

```Java
Dataset myDataset = new Dataset();
```

You need to use a DatasetFactory which will create automatically the right Dataset type (see: [Dataset types](https://github.com/tracymiranda/january-docs/blob/master/userguide/dataset-types.md)).

# Zero - Initialized Datasets

In the case that you want to create a Dataset with only zeros inside, you can do it like that:

```Java
Dataset myDataset = DatasetFactory.createFromObject(new int[] { 0, 0, 0, 0, 0, 0, 0, 0, 0 });
```

Or if you want to create it in multiple dimensions:

```Java
Dataset myDataset = DatasetFactory.createFromObject(new int[] { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 }, 2, 5);
```

Second parameter means that it will be a 2 dimensional array, and the third one means that it will split the data by 5 in each dimensions.
If you display the Dataset:

```Java
myDataset.toString(true);
```

The output should be:

```
Dataset [[0, 0, 0, 0, 0],
 [0, 0, 0, 0, 0]]
 ```
 
 **Note: you need to put ```Java true``` in the function to print dataset values.**

# One- Initialized Datasets

# Random Datasets

# Datasets from Arrays
    1. Create a 1D Dataset:
    
    2. Create a 2D Dataset:
    
    3. Create a ND Dataset:
 
# Creating Ranges

# Creating Datasets from other Datasets

# Miscellaneous examples

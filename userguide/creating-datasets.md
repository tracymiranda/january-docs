# Creating Datasets...

## Introduction

In this tutorial, we will explain you how to create divers Datasets from multiple types and multiple dimensions.
The Dataset class is an Abstract class, because of that, it's impossible to create a Dataset like that:

```Java
Dataset myDataset = new Dataset();
```

You need to use a DatasetFactory which will create automatically the right Dataset type (see: [Dataset types](https://github.com/tracymiranda/january-docs/blob/master/userguide/dataset-types.md)).

## Zero - Initialized Datasets

In the case that you want to create a Dataset with only zeros inside, you can do it with different ways:

### 1- 1D Zero Dataset

 #### 1. Manual way:

```Java
Dataset myDataset = DatasetFactory.createFromObject(new double[] { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 });
```

If you display the Dataset:

```Java
myDataset.toString(true);
```

The output should be:

```
Dataset [0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000]
```
 
**Note: you need to put ```true``` in the function to print dataset values.**



 #### 2. Automatic way:
 
```Java
Dataset myDataset = DatasetFactory.zeros(10);
```

The output should be:

```
Dataset [0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000]
```
 
### 2- Multidimensionnal Dataset

 #### 1. Manual way:

```Java
Dataset myDataset = DatasetFactory.createFromObject(new int[] { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 }, 2, 5);
```

or

```Java
Dataset myDataset = DatasetFactory.createFromObject(new int[][] {{ 0, 0, 0, 0, 0},{ 0, 0, 0, 0, 0 }});
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
 
 
 
 #### 2. Automatic way:
```Java
Dataset myDataset = DatasetFactory.zeros(2,5);
```

The output should be:

```
Dataset [[0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000],
 [0,0000000, 0,0000000, 0,0000000, 0,0000000, 0,0000000]]
```


## One - Initialized Datasets

In the case that you want to create a Dataset with only 1 as value, you can do like before with the manual solution, or directly:

```Java
Dataset myDataset = DatasetFactory.ones(9);
```
This should display:

```
Dataset [1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000]
```

**Note: Other parameters shown in "Zero - Initialized Datasets" works here too.**

## Random Datasets

In the case that you want to create a Dataset with random values, January provide a "Random" class that allow you to generate that, this is the steps you need to follow:

```Java
final int[] shape = new int[] {2, 4};
final Dataset myDataset = Random.randn(shape);
```

This will create a random Dataset with 2 dimensions 

## Datasets from Arrays
    1. Create a 1D Dataset:
    
    2. Create a 2D Dataset:
    
    3. Create a ND Dataset:
 
## Creating Ranges

## Creating Datasets from other Datasets

## Miscellaneous examples


final int[] shape = new int[] {1, 2, 3, 4};
		final Dataset d = Random.randn(shape);
		LazyDataset ld = LazyDataset.createLazyDataset(d);
  
  a = DatasetFactory.createFromObject(ComplexDoubleDataset.class, new double[] {0, 1, 2, 3, 4, 5});
  
  a = DatasetFactory.createFromObject(2, CompoundDoubleDataset.class, new double[] {0, 1, 2, 3, 4, 5});
  Compound dataset (2) [(0,0000000 1,0000000), (2,0000000 3,0000000), (4,0000000 5,0000000)]

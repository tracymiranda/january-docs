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


## One - Initialized Datasets

In the case that you want to create a Dataset with only 1 as value, you can do like before with the manual solution, or directly:

```Java
Dataset myDataset = DatasetFactory.ones(9);
```
This should display:

```
Dataset [1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000, 1,0000000]
```

## Random Datasets

In the case that you want to create a Dataset with random values, January provide a "Random" class that allow you to generate that, this is the steps you need to follow:

```Java
final int[] shape = new int[] {5};
final Dataset myDataset = Random.randn(shape);
```

This will create a random Dataset with 5 random values:

```
Dataset [-0,26948407, 0,35588735, -1,4729743, 0,49738359, 1,0261459]
```

## Datasets from Arrays
1- Create a 1D Dataset:
 
Like we saw before, the way to create a one dimensional Dataset is really easy, and works with all Java basic types:
```Java
byte, short, int, long, float, double
```
And all arrays of those types. Here we will use the double type.
 
So, to create a 1D Dataset, you just need to do:

```Java
double[] myDatasetValues = { 1.2, 2.3, 3.4, 4.5 };
Dataset myDataset = DatasetFactory.createFromObject(myDatasetValues);
```

This should return: ``` Dataset [1,2000000, 2,3000000, 3,4000000, 4,5000000] ```
 
2- Create a 2D Dataset:
    
Because a Dataset works with arrays, create a multidimensional Dataset is really easy, you just have to do:

```Java
double[][] myDatasetValues = {{ 1.2, 2.3}, {3.4, 4.5} };
Dataset myDataset = DatasetFactory.createFromObject(myDatasetValues);
```

But you can do that too:

```Java
Dataset myDataset = DatasetFactory.createFromObject(myDatasetValues, 2, 2);
```

Second parameter means that it will be a 2 dimensional array, and the third one means that it will split the data by 5 in each dimensions.

Those should return: 
```
Dataset [[1,2000000, 2,3000000],
 [3,4000000, 4,5000000]]
 ```
    
3- Create a ND Dataset:
    
To create a N dimensional Dataset, the concept is the same than before, you just give your array of your wanted dimension to the ```createFromObject()``` function:

```Java
double[][][][] myDatasetValues = 
	{{
		{{ 2, 4}, {4, 53},{ 12, 14}, {14 ,153}},
		{{ 3, 5}, {5, 54},{ 13, 15}, {15 ,154}}
	},
	{
		{{ 4, 6}, {6, 55},{ 14, 15}, {15 ,155}},
		{{ 5, 7}, {7, 56},{ 13, 16}, {16 ,156}}
	}};
Dataset myDataset = DatasetFactory.createFromObject(myDatasetValues);
```

You can also create it by this way :
```Java
double[] myDatasetValues = { 2, 4, 4, 53, 12, 14, 14, 153, 3, 5, 5, 54, 13, 15, 15, 154, 4, 6, 6, 55, 14, 15,
				15, 155, 5, 7, 7, 56, 13, 16, 16, 156 };
Dataset myDataset = DatasetFactory.createFromObject(myDatasetValues, 2,2,4,2);
```

Parameters explanation:
![explication](https://github.com/PierreSachot/Internship-Reports/blob/master/images/Screenshot_user_guide_creating_dataset.png?raw=true)

Every numbers correspond to the number of values to put inside of each dimensions.


If you print myDataset, the result would be:
```
Dataset [[[[2,0000000, 4,0000000],
   [4,0000000, 53,000000],
   [12,000000, 14,000000],
   [14,000000, 153,00000]],

  [[3,0000000, 5,0000000],
   [5,0000000, 54,000000],
   [13,000000, 15,000000],
   [15,000000, 154,00000]]],


 [[[4,0000000, 6,0000000],
   [6,0000000, 55,000000],
   [14,000000, 15,000000],
   [15,000000, 155,00000]],

  [[5,0000000, 7,0000000],
   [7,0000000, 56,000000],
   [13,000000, 16,000000],
   [16,000000, 156,00000]]]]
```
 
## Creating Ranges

January provides you the possibility to generate a Dataset with values started with a given start to a given stop, if you set only one parameter, the start will be automatically set to 0. The stop value is exclusive, this mean that it will generate the values to stop-1.

For example:

```Java
Dataset myDataset = DatasetFactory.createRange(20));
```

will generate:

```
Dataset [0,0000000, 1,0000000, 2,0000000, 3,0000000, 4,0000000, 5,0..., 15,000000, 16,000000, 17,000000, 18,000000, 19,000000]
```

To generate from a given start to a given stop, you need to do it like that:

```Java
Dataset myDataset = DatasetFactory.createRange(2,20, 1, DTypeUtils.getDType(DoubleDataset.class));
```
This will generate a DoubleDataset with values from 2 to 19 with a step of one:

```
Dataset [2,0000000, 3,0000000, 4,0000000, 5,0000000, 6,0000000, 7,0..., 15,000000, 16,000000, 17,000000, 18,000000, 19,000000]
```

## Creating Datasets from other Datasets

DatasetFactory allows you to create a new Dataset from an other Dataset, this means that all the values will be set in your new Dataset like in the previous one.

For that, you just have to pass the Dataset in parameters:

```Java
Dataset myDataset = Random.randn(new int[]{6});
Dataset myDataset2nd = DatasetFactory.createFromObject(myDataset);
System.out.println("First datase: "+myDataset.toString(true));
System.out.println("Second datase: "+myDataset2nd.toString(true));
```

This will display:
```Java
First datase: Dataset [-1,2232558, -0,25150990, 1,5683070, -1,5668022, 0,31399457, -0,32006293]
Second datase: Dataset [-1,2232558, -0,25150990, 1,5683070, -1,5668022, 0,31399457, -0,32006293]
``` 

---
title: "Pandas 2.0 - How to make your DataFrame manipulations super fast!"
date: 2024-07-15T11:30:00+00:00
tags: ["ML", "Data Science"]
author: "TomasCostaK"
description: "How Panda's new update will boost your Data transformations as a Data Practitioner"
cover:
    image: "covers/pandas.png"
    relative: true
showtoc: true
---
Panda's new update just dropped and with this new update, many new improvements were introduced.

JetBrain's Developer Survey shows that 55% of Python users, use Panda's library. Therefore, we know that this massive library adoption comes with a potential to give a lot of performance boost to everyone using it. This is exactly the main point of this new 2.0.0 update.

## Pandas 2.0.0

The main change to Panda's 2.0.0 that we will be covered in this article is the new backend support for Apache Arrow.

For many years, the main extension to represent arrays and perform operations on them in a fast way has been NumPy. And this is what pandas was initially built on.

And although NumPy has been instrumental in making pandas the widely-used library it is today, it wasn't designed to be a backend for dataframe libraries, and it has several notable shortcomings. For instance, it provides limited support for strings and doesn't include a native mechanism for handling missing values.

Dealing with missing (null) values in pandas has been challenging, partially since it doesn't allow null values for certain data types, such as integer dtypes. Consequently, introducing a null value in an integer column caused the entire column to be converted to a float dtype. This sudden conversion from integer to float was far from ideal. This is just one of the points that Arrow solves.

## What is Apache Arrow?

According to Apache Arrow's [website](https://arrow.apache.org/):

> "Apache Arrow defines a language-independent columnar memory format for flat and hierarchical data, organized for efficient analytic operations on modern hardware like CPUs and GPUs. The Arrow memory format also supports zero-copy reads for lightning-fast data access without serialization overhead."

This means that the format is language-independent and there is no need to make copy and conversion operations between different data types. This makes it a great format to perform in-memory analytics, something that most Data Science practitioners perform daily.

![Image displaying Arrow's Memory conversion between data types vs. traditional](../images/pandas_img1.png "Arrow Memory conversion between data types vs. traditional (from Apache Arrow Website)")

Columnar data stores are designed to store data in a way that groups related columns together in memory. This results in faster data operations such as calculating the average value of a column. Additionally, Arrow data types also include helpful features such as treatment for missing values and interoperability, which will are discussed below.

## Why is this important?

There's several important new additions with the PyArrow change, below are some of the most notable ones.

### Missing values

As we have mentioned previously, missing values are a complex topic.

Initially, pandas handled missing values by converting numbers to floating point and using NaN. However, this approach had limitations, particularly when converting integers to floating point.

With the introduction of extension arrays, pandas added its own data types for missing values using two arrays, one for the data and another for boolean values indicating presence or absence of data.

This approach is similar to the one used by Apache Arrow's in-memory data representation. By using Arrow, pandas can manage missing values across data types without creating its own version for each type.

### Interoperability

Like a CSV file, Arrow is a universal data format that is compatible with various programs such as pandas, R, and Excel. Despite being an in-memory format instead of a file format, Arrow's open specification makes it accessible to different consumers even without a file extension.

This has two significant benefits: it allows for easy sharing of data between programs, and it enables fast and memory-efficient data sharing by multiple programs accessing the same memory instead of creating separate copies.

### Speed

All of this means that the new columnar format should show large improvements when it comes to manipulation of the data. Below is a table showing the speedups that were tested on this new pandas version, using both NumPy and PyArrow.

## Speedup Demonstration

So how can you start using this in your own code? First of all you will need to update to the most recent version of pandas:

```bash
pip install "pandas>=2.0.0"
# You might also need to download this
pip install pyarrow
```

After you have the most recent version of pandas you can run some quick examples to see how much this new change can influence your daily workflow. The following example is from reading a database with 500,000 rows, 41 columns with numerical and categorical data.

Then, all you need to do is read data with the pyarrow engine, like the following:

```python
df = pd.read_csv(fname)
df_pyarrow = pd.read_csv(fname, engine='pyarrow', dtype_backend='pyarrow')
```

After experimenting some common manipulations of data, specially with strings, the following table was created:

![Table comparison of speedup times](../images/pandas_img2.png "Timing of common operations using %%timeit")

These results clearly show a huge improvement when it comes to string manipulation, but also when reading from large files. Panda's 2.0.0 will be a great addition to your everyday workflow!
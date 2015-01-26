# csv2tensor
A simple utility to transform a CSV file into a [Torch7](http://torch.ch) Tensor

*csv2tensor* assumes that you are working with CSV files containing only headers and and numeric data.

basic usage is to simply load the csv file into a torch.Tensor. Since the initial order of the columns in the CSV file is not guaranteed the *load* function also returns a list of column names in the orderthey appear in the tensor

<code>
csv2tensor = require 'csv2tensor'

training_tensor, column_names = csv2tensor.load("training.csv")
</code>

*csv2tensor* also allow you to exclude certain columns by an optional parameter.

<code>
no_label_tensor, column_names = csv2tensor.load("training.csv",{exclude={"label"})    
</code>

In addition you can also include only specific columns (as shown in the example this is useful if you have a label in your csv)

<code>
labels_tensor = csv2tensor.load("training.csv",{include={"label"})    
</code>

Note: in it's current state *csv2tensor* assumes you have done all the hard work and have a very straightforward CSV file, NA values, non number values, etc will cause errors. But for straightforward, numberic csv files this should make things a bit easier.

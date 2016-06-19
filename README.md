# analysistoolbox
My implementation of various techniques to streamline my future data science projects. 

## onehotencoder.R
This function will read a data frame in the format where rows are observations and columns are attributes. 
It will return an equivalent matrix of binary attributes that encodes the categorical attributes of the data
frame into an expanded set of binary-encoded attributes. This is a frequent pre-processing measure to 
run a regression model whose variables are categorical rather than numeric. 

For example, if a regression problem wanted to predict the value of some objection function dependent on the 
presence of a certain color, where "color" is a categorical variable take only takes values "red", "green", 
and "blue", this will will be converted into a 3 attribute data frame taking the names of each categorical label.
For each row, a "red" observation would be encoded as [1 0 0], a "blue" observation would be [0 1 0] and "green" 
would be [0 0 1]. This function is useful for categorical attributes that take many values, perhaps an unknown
number of different labels that would be infeasible for the analyst to examine manually. 

A precondition to using this function is that only the columns you are interested in should be included: otherwise, 
the resulting matrix may blow up with many more binary attribute columns than needed. This function assumes that 
the attributes you want to be one-hot encoded are already factor variables. If they are numeric variables or some
other type, the variable will be included in the output matrix, but will remain unchanged. 

It appears that running this function will exceed the memory capacity of the computer if more than 100000 rows are
processed. The implementation was adopted from a post in Stack Overflow.

Link: http://stackoverflow.com/questions/4560459/all-levels-of-a-factor-in-a-model-matrix-in-r
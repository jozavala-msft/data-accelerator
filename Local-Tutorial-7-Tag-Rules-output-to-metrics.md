In this tutorial, you'll learn to:
 - Create a tag rule without writing code

# Creating a rule 
 - Open your Flow
 - Go to Rules tab, and click Add a "Tag Rule".  
 - Set a Description for the rule and a tag to describe the rule.  This will be additional metadata being added to rows of the input table DataXProcessInput.
 - In conditions, select the column of data to monitor and set the condition to measure against.  i.e. select 'temperature' in the column, select '>' and 60.  This would trigger the rule when the temperature value is above 60.
 - In the Query tab, add the following, before the OUTPUT statements

	--DataXQuery--
	T1 = ProcessRules(DataXProcessedInput);
	
 - Click Deploy

T1 will now contain the DataXProcessedInput data, along with tags from the rules set in this Flow

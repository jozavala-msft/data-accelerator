For various kinds of analysis, business insights, technical insights, cohort analysis, etc. it is important to analyze and "Tag" the streaming data. Downstream processing can then take advantage of these tags for immediate action or down the road insights. 

In this tutorial, you'll learn to:
 - Create a tag rule without writing code

# Creating a rule 
 - Open your Flow
 - Go to Rules tab, and click Add a "Tag Rule". <br/>
![Add Rule](./tutorials/images/addrule.png)
 - Set a Description for the rule and a tag to describe the rule.  This will be additional metadata being added to rows of the input table DataXProcessInput.
 - In conditions, select the column of data to monitor and set the condition to measure against.  i.e. select 'temperature' in the column, select '>' and 60.  This would trigger the rule when the temperature value is above 60.
![Add Rule Warm](./tutorials/images/addrulewarm.png)
 - In the Query tab, add the following, before the other OUTPUT statement:

	--DataXQuery--<br/>
	T1 = ProcessRules(DataXProcessedInput);
        
        OUTPUT T1 TO myOutput;
<br/>
 ![Rules Query](./tutorials/images/rulesquery.png)
 - Click Deploy

T1 will now contain the DataXProcessedInput data, along with tags from the rules set in this Flow.  You can view the data flowing in the location defined in the previous tutorial.

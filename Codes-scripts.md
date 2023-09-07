# Code for transforming/Flattening the raw dataset given
 
1.	import pandas as pd
2.	import json
3.	
4.	def flatten(df, col_dim, row_dim, value_dim):
5.	    entries = []
6.	    for col in df.columns:
7.	        print(f'parsing column {col} ...')
8.	        for row in df.index:
9.	            entry = {
10.	                col_dim: col,
11.	                row_dim: row,
12.	                value_dim: df[col].loc[row]
13.	            }
14.	            entries.append(entry)
15.	
16.	    return pd.DataFrame(entries)
17.	
18.	if __name__=='__main__':
19.	    config = json.load(open('flatten_config.json', 'r'))
20.	    df = pd.read_excel(config['file_name'], index_col=0)
21.	
22.	    df_flat = flatten(df=df,  
23.	                      col_dim=config['column_dimension'],
24.	                      row_dim=config['row_dimension'],   
25.	                      value_dim=config['value_dimension']
26.	              )
27.	
28.	    output_name = config['file_name'].split('.')[0] + '_flat.xlsx'
29.	
30.	    df_flat.to_excel(output_name)

# Code for creating additional columns
1.	{
2.   "file_name": "wikipedia_dataset.xlsx",
3	    "column_dimension": "date",
5.	    "row_dimension": "page",
6.	    "value1_dimension": "visits",
7.	    "value2_dimension": "page_language",
8.	    "value3_dimension": "access_device_type",
9.	    "value4_dimension": "day_of_the_week",
10.	    "value5_dimension": "month"
11.	}







```python
#set dependencies
import pandas as pd

```


```python
#set file path
jsonpath = ('../NUCHI201801DATA4-Class-Repository-DATA/MWS/Homework/04-Numpy-Pandas/Instructions/HeroesOfPymoli/purchase_data.json')
```


```python
#read the file
data_df = pd.read_json(jsonpath)
data_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>




```python
#find total number of players
total_players = data_df['SN'].nunique()
df_1 = pd.DataFrame({"Total Players":[total_players]})
df_1
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>573</td>
    </tr>
  </tbody>
</table>
</div>




```python
#extract unique players
unique_players = data_df.drop_duplicates(subset=['SN'], keep='first')
unique_players.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>




```python
#find number of unique items
unique_items = data_df['Item ID'].nunique()


```


```python
#find the average purchase price
average_purchase_price = round(data_df['Price'].mean(),2)

```


```python
#find the total number of purchases
total_purchases = len(data_df['Price'])

```


```python
#find the total revenue
total_revenue = sum(data_df['Price'])
                        
```


```python
#consolidated purchasing analysis
df_2 = pd.DataFrame({"Unique Items":[unique_items],
                    "Avg Purchase Price":[average_purchase_price],
                    "Total Number of Purchases":[total_purchases],
                    "Total Revenue":[total_revenue]})
df_2 = df_2[['Unique Items', 'Avg Purchase Price', 'Total Number of Purchases', 'Total Revenue']]
df_2
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unique Items</th>
      <th>Avg Purchase Price</th>
      <th>Total Number of Purchases</th>
      <th>Total Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>183</td>
      <td>2.93</td>
      <td>780</td>
      <td>2286.33</td>
    </tr>
  </tbody>
</table>
</div>




```python
#find percentage and Count of Male Players

total = unique_players['Gender'].count()

male_count = unique_players["Gender"].value_counts()['Male']
percent_male = round(male_count / total * 100,0)

#find percentage and count of female players
female_count = unique_players['Gender'].value_counts()['Female']
percent_female = round(female_count / total * 100,0)

#find percentage and count of other/non-disclosed players
other_count = unique_players['Gender'].value_counts()['Other / Non-Disclosed']
percent_other = round(other_count / total * 100,0)
```


```python
df_3 = pd.DataFrame({"Percentage of Players":[percent_male, percent_female, percent_other],
                    "Count of Players":[male_count, female_count, other_count]},
                   index = ['Male', 'Female', 'Other/Non-Disclosed'])
df_3

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count of Players</th>
      <th>Percentage of Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>465</td>
      <td>81.0</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>100</td>
      <td>17.0</td>
    </tr>
    <tr>
      <th>Other/Non-Disclosed</th>
      <td>8</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#find the purchase count, avg purchase price, total purchase value, and normalized totals by gender
male_purchases = data_df.loc[data_df['Gender'] == 'Male']
male_purchase_count = len(male_purchases)
male_avg_price = round(male_purchases['Price'].mean(),2)
male_total_value = sum(round(male_purchases['Price']),2)
male_norm = round(male_total_value / male_purchase_count,2)

female_purchases = data_df.loc[data_df['Gender'] == 'Female']
female_purchase_count = len(female_purchases)
female_avg_price = round(female_purchases['Price'].mean(),2)
female_total_value = sum(round(female_purchases['Price']),2)
female_norm = round(female_total_value / female_purchase_count,2)

other_purchases = data_df.loc[data_df['Gender'] == 'Other / Non-Disclosed']
other_purchase_count = len(other_purchases)
other_avg_price = round(other_purchases['Price'].mean(),2)
other_total_value = sum(round(other_purchases['Price']),2)
other_norm = round(other_total_value / other_purchase_count,2)

```


```python
#purchasing analysis
df_4 = pd.DataFrame({'Purchase Count':[male_purchase_count, female_purchase_count, other_purchase_count],
                    'Avg Purchase Price':[male_avg_price, female_avg_price, other_avg_price],
                    'Total Purchase Value':[male_total_value, female_total_value, other_total_value],
                    'Normalized Totals':[male_norm, female_norm, other_norm]},
                   index = ['Male', 'Female', 'Other/Non-Disclosed'])

purchasing_df = df_4[['Purchase Count', 'Avg Purchase Price', 'Total Purchase Value', 'Normalized Totals']]
purchasing_df
 
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase Count</th>
      <th>Avg Purchase Price</th>
      <th>Total Purchase Value</th>
      <th>Normalized Totals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>633</td>
      <td>2.95</td>
      <td>1862.0</td>
      <td>2.94</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>136</td>
      <td>2.82</td>
      <td>387.0</td>
      <td>2.85</td>
    </tr>
    <tr>
      <th>Other/Non-Disclosed</th>
      <td>11</td>
      <td>3.25</td>
      <td>37.0</td>
      <td>3.36</td>
    </tr>
  </tbody>
</table>
</div>




```python
#The below each broken into bins of 4 years (i.e. &lt;10, 10-14, 15-19, etc.) 
  # Purchase Count
  # Average Purchase Price
  # Total Purchase Value
  # Normalized Totals

bins = [0, 9, 14, 19, 24, 29, 34, 39, 100]
group_names = [' < 10', '10-14', '15-19', '20-24', '25-29', '30-34', '35-39', '40+']

age_range = pd.cut(data_df["Age"], bins, labels=group_names)
data_df['Age Range'] = pd.cut(data_df["Age"], bins, labels=group_names)

```


```python
#age demographics
age_demographics = data_df.groupby('Age Range')
age_demographics.count()
age_purchase_count = age_demographics['Item ID'].count()
age_avg_purchase_price = round(age_demographics['Price'].mean(),2)
age_total_value = age_demographics['Price'].sum()
age_norm = round(age_total_value / age_purchase_count,2)

age_df = pd.DataFrame({'Purchase Count':age_purchase_count,
                      'Average Purchase Price':age_avg_purchase_price,
                      'Total Purchase Value':age_total_value,
                      'Normalized Totals':age_norm})
age_demographics = age_df[['Purchase Count', 'Average Purchase Price', 'Total Purchase Value', 'Normalized Totals']]
age_demographics
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase Count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase Value</th>
      <th>Normalized Totals</th>
    </tr>
    <tr>
      <th>Age Range</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt; 10</th>
      <td>28</td>
      <td>2.98</td>
      <td>83.46</td>
      <td>2.98</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>35</td>
      <td>2.77</td>
      <td>96.95</td>
      <td>2.77</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>133</td>
      <td>2.91</td>
      <td>386.42</td>
      <td>2.91</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>336</td>
      <td>2.91</td>
      <td>978.77</td>
      <td>2.91</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>125</td>
      <td>2.96</td>
      <td>370.33</td>
      <td>2.96</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>64</td>
      <td>3.08</td>
      <td>197.25</td>
      <td>3.08</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>42</td>
      <td>2.84</td>
      <td>119.40</td>
      <td>2.84</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>17</td>
      <td>3.16</td>
      <td>53.75</td>
      <td>3.16</td>
    </tr>
  </tbody>
</table>
</div>




```python
#group purchases by SN
#SN
#Purchase Count
#Average Purchase Price
#Total Purchase Value
grouped_df = data_df.groupby(['SN'])

purchase_count = grouped_df['Item ID'].count()
average_purchase_price = round(grouped_df['Price'].mean(),2)
total_purchase_value = round(grouped_df['Price'].sum(),2)

purchase_df = pd.DataFrame({
                           'Purchase Count':purchase_count,
                           'Average Purchase Price':average_purchase_price,
                           'Total Purchase Value':total_purchase_value})

```


```python
#top spenders
top_spenders= purchase_df.sort_values('Total Purchase Value', ascending=False)
top_spenders.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Purchase Price</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Undirrala66</th>
      <td>3.41</td>
      <td>5</td>
      <td>17.06</td>
    </tr>
    <tr>
      <th>Saedue76</th>
      <td>3.39</td>
      <td>4</td>
      <td>13.56</td>
    </tr>
    <tr>
      <th>Mindimnya67</th>
      <td>3.18</td>
      <td>4</td>
      <td>12.74</td>
    </tr>
    <tr>
      <th>Haellysu29</th>
      <td>4.24</td>
      <td>3</td>
      <td>12.73</td>
    </tr>
    <tr>
      <th>Eoda93</th>
      <td>3.86</td>
      <td>3</td>
      <td>11.58</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Identify the 5 most popular items by purchase count, then list (in a table):
#Item ID
#Item Name
#Purchase Count
#Item Price
#Total Purchase Value
item_df = data_df.groupby(['Item ID','Item Name'])
item_count = item_df['Item ID'].count()
purchase_value = item_df['Price'].sum()
item_price = round(purchase_value / item_count,2)

popular_df = pd.DataFrame({'Purchase Count':item_count,
                          'Item Price':item_price,
                          'Total Purchase Value':purchase_value})
```


```python
#popular items
popular_items = popular_df.sort_values('Purchase Count', ascending=False)
popular_items.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Item Price</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>39</th>
      <th>Betrayal, Whisper of Grieving Widows</th>
      <td>2.35</td>
      <td>11</td>
      <td>25.85</td>
    </tr>
    <tr>
      <th>84</th>
      <th>Arcane Gem</th>
      <td>2.23</td>
      <td>11</td>
      <td>24.53</td>
    </tr>
    <tr>
      <th>31</th>
      <th>Trickster</th>
      <td>2.07</td>
      <td>9</td>
      <td>18.63</td>
    </tr>
    <tr>
      <th>175</th>
      <th>Woeful Adamantite Claymore</th>
      <td>1.24</td>
      <td>9</td>
      <td>11.16</td>
    </tr>
    <tr>
      <th>13</th>
      <th>Serenity</th>
      <td>1.49</td>
      <td>9</td>
      <td>13.41</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Identify the 5 most profitable items by total purchase value, then list (in a table):
#Item ID
#Item Name
#Purchase Count
#Item Price
#Total Purchase Value
profitable_items = popular_df.sort_values('Total Purchase Value', ascending=False)
profitable_items.head()

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Item Price</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>34</th>
      <th>Retribution Axe</th>
      <td>4.14</td>
      <td>9</td>
      <td>37.26</td>
    </tr>
    <tr>
      <th>115</th>
      <th>Spectral Diamond Doomblade</th>
      <td>4.25</td>
      <td>7</td>
      <td>29.75</td>
    </tr>
    <tr>
      <th>32</th>
      <th>Orenmir</th>
      <td>4.95</td>
      <td>6</td>
      <td>29.70</td>
    </tr>
    <tr>
      <th>103</th>
      <th>Singed Scalpel</th>
      <td>4.87</td>
      <td>6</td>
      <td>29.22</td>
    </tr>
    <tr>
      <th>107</th>
      <th>Splitter, Foe Of Subtlety</th>
      <td>3.61</td>
      <td>8</td>
      <td>28.88</td>
    </tr>
  </tbody>
</table>
</div>



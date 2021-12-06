# DDM5051 Project 2

- Group 8
- WONG Ryan, ZHAO Jiawei, CHEN Xinyi
- Version: 1.0, date: 06/12/2021

## 1. UML design
<div align=center>
    <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig1.png" >
</div>

<style>
table {
margin: auto;
}
</style>

### 1.1 View
The main function of view object is to display the user interface. We use the ‘streamlit’ library which is easy to build a web and share data in Python.

<table class="tg">
<thead>
  <tr>
    <th class="tg-o5sn"></th>
    <th class="tg-27gm"><span style="font-weight:700;text-decoration:none;color:white;background-color:#A5A5A5">Name</span></th>
    <th class="tg-27gm"><span style="font-weight:700;text-decoration:none;color:white;background-color:#A5A5A5">Function</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-grpo">Attributes</td>
    <td class="tg-g60y">data_handler</td>
    <td class="tg-g60y">process&nbsp;&nbsp;&nbsp;data</td>
  </tr>
  <tr>
    <td class="tg-z1yq" rowspan="9">Operations</td>
    <td class="tg-vask">fetch_data</td>
    <td class="tg-vask">read data from local path</td>
  </tr>
  <tr>
    <td class="tg-g60y">capture_time() </td>
    <td class="tg-2xum"><span style="font-weight:400;text-decoration:none;color:black;background-color:#EDEDED">return search/sort time consuming</span></td>
  </tr>
  <tr>
    <td class="tg-vask">render()</td>
    <td class="tg-vask">display user interface</td>
  </tr>
  <tr>
    <td class="tg-g60y">on_search(target_col,&nbsp;&nbsp;&nbsp;keyword)</td>
    <td class="tg-2xum"><span style="font-weight:400;text-decoration:none;color:black;background-color:#EDEDED">check input</span></td>
  </tr>
  <tr>
    <td class="tg-vask">on_sort(target_col,&nbsp;&nbsp;&nbsp;way, top_n)</td>
    <td class="tg-nvy4"><span style="font-weight:400;text-decoration:none;color:black">check input</span></td>
  </tr>
  <tr>
    <td class="tg-g60y">display_results(name_in_state:&nbsp;&nbsp;&nbsp;str) </td>
    <td class="tg-2xum"><span style="font-weight:400;text-decoration:none;color:black;background-color:#EDEDED">display pagination of large&nbsp;&nbsp;&nbsp;amount of results on web</span></td>
  </tr>
  <tr>
    <td class="tg-vask">display_description</td>
    <td class="tg-nvy4"><span style="font-weight:400;text-decoration:none;color:black">display column description on web</span></td>
  </tr>
  <tr>
    <td class="tg-g60y">display_search</td>
    <td class="tg-2xum"><span style="font-weight:400;text-decoration:none;color:black;background-color:#EDEDED">disply search interface and&nbsp;&nbsp;&nbsp;search results on web</span></td>
  </tr>
  <tr>
    <td class="tg-vask">display_sort</td>
    <td class="tg-nvy4"><span style="font-weight:400;text-decoration:none;color:black">disply sort interface and&nbsp;&nbsp;&nbsp;sort results on web</span></td>
  </tr>
</tbody>
</table>

### 1.2 TrafficData
The main function of this part is to read data from .csv and return it in pandas.dataframe format.

<table class="tg">
<thead>
  <tr>
    <th class="tg-o5sn"></th>
    <th class="tg-9tzt"><span style="font-weight:700;text-decoration:none;color:white;background-color:#A5A5A5">Name</span></th>
    <th class="tg-9tzt"><span style="font-weight:700;text-decoration:none;color:white;background-color:#A5A5A5">Function</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-6pjd">Attributes</td>
    <td class="tg-v7s9">data:pandas.dataframe</td>
    <td class="tg-hl7b"><span style="font-weight:400;text-decoration:none;color:black;background-color:#EDEDED">None</span></td>
  </tr>
  <tr>
    <td class="tg-baqh">Operations</td>
    <td class="tg-0lax">from_file()</td>
    <td class="tg-0lax">read .csv from local path and return a dataframe</td>
  </tr>
</tbody>
</table>

### 1.3 TrafficDataHandler
This part is for sorting and searching. We use the sort and search functions in pandas.

<table class="tg">
<thead>
  <tr>
    <th class="tg-o5sn"></th>
    <th class="tg-9tzt"><span style="font-weight:700;text-decoration:none;color:white;background-color:#A5A5A5">Name</span></th>
    <th class="tg-9tzt"><span style="font-weight:700;text-decoration:none;color:white;background-color:#A5A5A5">Function</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-6pjd">Attributes</td>
    <td class="tg-v7s9">None</td>
    <td class="tg-v7s9">None</td>
  </tr>
  <tr>
    <td class="tg-baqh" rowspan="2">Operations</td>
    <td class="tg-0lax">search()</td>
    <td class="tg-0lax">return lines containing the keyword</td>
  </tr>
  <tr>
    <td class="tg-v7s9">sort()</td>
    <td class="tg-v7s9">sort the&nbsp;&nbsp;&nbsp;chosen column, return the sorted dataframe</td>
  </tr>
</tbody>
</table>

## 2. Interface design
The whole interface designing progress is rely on the Python open source library – streamlit (st for short)
<div align=center>
    <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig2_1.png" width = "500">
</div>

### 2.1 Title
We use `st.header` to display the title.
```python
st.header('🚥Inquiry System For Taiwan Traffic Data🚦')
```

### 2.2 Data preview
This part displays a small fraction of dataset and the column descriptions in order to introduce the data structure to users.

<div align=center>
    <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig2_2.png" width = "500">
</div>

```python
def render(self):
    ############ loading the data
    with st.expander('Expand to peek the data and columns description.'):
        self._display_data_description()
def _display_data_description(self):
    st.markdown("#### First 5 rows of the dataset")
    st.write(st.session_state.traffic_df.head())
    st.markdown("""
    #### Column descriptions:
    |  Columns |  Descriptions |
    |---|---|
    | 'VehicleType' |  車種，31小客車、32小貨車、41大客車、42大貨車、5聯結車 |
    | 'DerectionTime_O' |  車輛通過本旅次第1個測站時間 |
    | 'GantryID_D' | 車輛通過本旅次第1個測站編號 |
    | 'DerectionTime_D' |  車輛通過本旅次最後1個測站時間 |
    | 'TripLength' | 本旅次行駛距離  |
    | 'TripEnd' | 旅次標記(Y正常結束，N異常)  |
    | 'TripInformation' |  本旅次經過各個測站之通過時間及編號 |
    
    """)

```

### 2.3 Search part
In search part, users will:

1. choose a column which contains the searching target
2. input the searching keyword

And our server will show all lines contain the keyword.

```python
def _display_search(self):
   st.markdown("### SEARCH")
   search_spaces1, search_spaces2 = st.columns([1, 1])

   search_target = search_spaces1.selectbox(
      "Search a record", st.session_state.traffic_df.columns)
   is_search = search_spaces1.button("Search 🔍", )
   if search_target in ['DerectionTime_O', 'DerectionTime_D']:
      search_keyword = search_spaces2.text_input(
          " ", placeholder="(YYYY-MM-DD HH:MM:SS)"
      )
   else:
      search_keyword = search_spaces2.text_input(
          "keyword", placeholder="Input your keyword"
      )

   if is_search:
      with st.spinner(f'Searching: {search_keyword} ...'):
          result = self.on_search(search_target, search_keyword)
          st.session_state.search_result = result
   if st.session_state.get('search_result') is not None:
      st.subheader("Search results:")
      self.display_results('search_result')
```

### 2.4 Sort part

The appearance of sort part is similar to the search one. Here users will:

1. choose a column which is expected to be sorted
2. choose the sort way (ascending or non-ascending)
3. input the Max. number of items (for example, show the top3 largest items)

And our server will return a sorted dataframe.

```python
def _display_sort(self):
   st.markdown("### SORT")
   sort_spaces1, sort_spaces2, sort_spaces3 = st.columns(3)

   sort_target = sort_spaces1.selectbox(
      "Sort a record", st.session_state.traffic_df.columns, key = "<aaa>")
   sort_way = sort_spaces2.selectbox(
      "Ascending order or not", ['ascending', 'descending'])
   sort_display_num = sort_spaces3.text_input(
      "Max. number of items", placeholder="default: 10")
   is_sort = sort_spaces1.button("Sort 🔍")

   if is_sort:
      result = self.on_sort(sort_target, sort_way, sort_display_num)
      st.session_state.sort_result = result
   if st.session_state.get('sort_result') is not None:
      st.subheader("Sort results:")
      self.display_results('sort_result')
```

## 3. Function design

Function part contains search and sort, which are realized based on Pandas.

To be noticed, when users do searching, firstly our function will check every element which is equal to the keyword strictly. If there is no result, it will check the elements which contain the keyword. For example, if you search the keyword '2019-08', all dates in Aug. 2019 will be returned.


```python
class TrafficDataHandler:
    def search(self, df, column, keyword):
        r = df[df[column].isin([keyword])]
        if r.empty:
            return df[df[column].astype(str).str.contains(keyword)]
        return r

    def sort(self, df, column, way, num):
        if way == 'ascending':
            acd = True
        elif way == 'non-ascending':
            acd = False
        return df.sort_values(by=[column], ascending=acd)[:num]
```

## 4. Run example

### 4.1 Search

1. when user inputs the legal information, the result will return in a dataframe.
   - search a date
   <div align=center>
       <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig4_1.png" width = "600">
   </div>

   - search a gantryID
   <div align=center>
       <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig4_2.png" width = "500">
   </div>
   
2. when user inputs an empty string, warining info will be shown.
   <div align=center>
       <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig4_3.png" width = "500">
   </div>

### 4.1 Sort

1. the top 3 longest trip length
   <div align=center>
       <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig4_4.png" width = "500">
   </div>
2. the top 100 smallest vehicle type
   <div align=center>
       <img src="https://github.com/jiaweizh-823/5056project2/raw/main/figs/fig4_5.png" width = "500">
   </div>

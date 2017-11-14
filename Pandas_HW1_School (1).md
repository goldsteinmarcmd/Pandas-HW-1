

```python
import pandas as pd
import os
```


```python
csv_path = os.path.join('schools_complete.csv')
```


```python
schools_df = pd.read_csv(csv_path)
schools_df.head(5)
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
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
csv_path = os.path.join('students_complete.csv')
```


```python
students_df = pd.read_csv(csv_path)
students_df.head(5)
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
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
students_df.columns
```




    Index(['Student ID', 'name', 'gender', 'grade', 'school', 'reading_score',
           'math_score'],
          dtype='object')




```python
schools_df.columns
```




    Index(['School ID', 'name', 'type', 'size', 'budget'], dtype='object')




```python
merge_table = pd.merge(students_df, schools_df, left_on=['school'], right_on=['name'])
merge_table.head()
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
      <th>Student ID</th>
      <th>name_x</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>name_y</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
  </tbody>
</table>
</div>




```python
#district summary
math_score_mean = merge_table['math_score'].mean()
math_score_mean
reading_score_mean = merge_table['reading_score'].mean()
reading_score_mean
budget = merge_table['budget'].sum()
budget
total_students = merge_table['Student ID'].count()
total_students
school_count =merge_table['school'].nunique()
school_count

passing_math = merge_table.loc[merge_table["math_score"]>69, ["math_score"]]
passing_math["math_score"].count()
passing_math_count = passing_math["math_score"].count()
passing_math_count
passing_math_rate = passing_math_count/total_students
passing_math_rate

passing_reading = merge_table.loc[merge_table["reading_score"]>69, ["reading_score"]]
passing_reading["reading_score"].count()
passing_reading_count = passing_reading["reading_score"].count()
passing_reading_count
passing_reading_rate = passing_reading_count/total_students
passing_reading_rate
overall_passing_rate = ((passing_reading_rate + passing_math_rate)/2)*100
overall_passing_rate
summary_table = pd.DataFrame({"Math Score Mean": [math_score_mean],
                              "Reading Score Mean": [reading_score_mean],
                              "Total Budget": [budget],
                              "Total Students": [total_students],
                              "Total Schools": [school_count],
                              "Passing Math Rate": [passing_math_rate],
                              "Passing Reading Rate" : [passing_reading_rate],
                              "Overall Passing Rate" : [overall_passing_rate]
                              })
summary_table
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
      <th>Math Score Mean</th>
      <th>Overall Passing Rate</th>
      <th>Passing Math Rate</th>
      <th>Passing Reading Rate</th>
      <th>Reading Score Mean</th>
      <th>Total Budget</th>
      <th>Total Schools</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>78.985371</td>
      <td>80.393158</td>
      <td>0.749809</td>
      <td>0.858055</td>
      <td>81.87784</td>
      <td>82932329558</td>
      <td>15</td>
      <td>39170</td>
    </tr>
  </tbody>
</table>
</div>




```python
#school summary
##Create an overview table that summarizes key metrics about each school, including:
school_summary = merge_table.groupby(['school', 'type'])
school_summary.head()
school_budget = school_summary["budget"].unique()
school_budget
#Average Math Score
average_math_score = school_summary["math_score"].mean()
average_math_score
#Average Reading Score
average_reading_score = school_summary["reading_score"].mean()
#Total Students
total_students = school_summary["Student ID"].count()
total_students
#Per Student Budget
per_student_budget = school_budget/total_students
per_student_budget

#% Passing Math
#passing_math = school_summary.loc[school_summary["math_score"]>69, ["math_score"]]
#passing_math["math_score"].count()
#passing_math_count = passing_math["math_score"].count()
#passing_math_count
#passing_math_rate = passing_math_count/total_students
#passing_math_rate


#% Passing Reading
#passing_reading = school_summary.loc[school_summary["reading_score"]>69, ["reading_score"]]
#passing_reading["reading_score"].count()
#passing_reading_count = passing_reading["reading_score"].count()
#passing_reading_count
#passing_reading_rate = passing_reading_count/total_students
#passing_reading_rate

#Overall Passing Rate (Average of the above two)
#overall_passing_rate = ((passing_reading_rate + passing_math_rate)/2)*100
#overall_passing_rate

school_summary_table = pd.DataFrame({"School Budget": school_budget,
                              "Average Math Score": average_math_score,
                              "Average Reading Score": average_reading_score,
                              "Total Students": total_students,
                              "Per Student Budget": per_student_budget,
#                             "Passing Math Rate": passing_math_rate,
#                              "Passing Reading Rate": passing_reading_rate,
#                              "Total Schools": [school_count]
                             })

school_summary_table
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
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Per Student Budget</th>
      <th>School Budget</th>
      <th>Total Students</th>
    </tr>
    <tr>
      <th>school</th>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <th>District</th>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>[628.0]</td>
      <td>[3124928]</td>
      <td>4976</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <th>Charter</th>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>[582.0]</td>
      <td>[1081356]</td>
      <td>1858</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <th>District</th>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>[639.0]</td>
      <td>[1884411]</td>
      <td>2949</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <th>District</th>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>[644.0]</td>
      <td>[1763916]</td>
      <td>2739</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <th>Charter</th>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>[625.0]</td>
      <td>[917500]</td>
      <td>1468</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <th>District</th>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>[652.0]</td>
      <td>[3022020]</td>
      <td>4635</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <th>Charter</th>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>[581.0]</td>
      <td>[248087]</td>
      <td>427</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <th>District</th>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>[655.0]</td>
      <td>[1910635]</td>
      <td>2917</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <th>District</th>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>[650.0]</td>
      <td>[3094650]</td>
      <td>4761</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <th>Charter</th>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>[609.0]</td>
      <td>[585858]</td>
      <td>962</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <th>District</th>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>[637.0]</td>
      <td>[2547363]</td>
      <td>3999</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <th>Charter</th>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>[600.0]</td>
      <td>[1056600]</td>
      <td>1761</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <th>Charter</th>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>[638.0]</td>
      <td>[1043130]</td>
      <td>1635</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <th>Charter</th>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>[578.0]</td>
      <td>[1319574]</td>
      <td>2283</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <th>Charter</th>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>[583.0]</td>
      <td>[1049400]</td>
      <td>1800</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Top Performing Schools (By Passing Rate)
#Create a table that highlights the top 5 performing schools based on Overall Passing Rate. 

#Include:
#School Name
#School Type
#Total Students
#Total School Budget
#Per School Budget
#Average Math Score
#Average Reading Score
#% Passing Math
#% Passing Reading
#Overall Passing Rate (Average of the above two)
```


```python
#Top Performing Schools (By Passing Rate)
#Create a table that highlights the bottom 5 performing schools 
#based on Overall Passing Rate. Include all of the same metrics as above.
```


```python
#Math Scores by Grade
#Create a table that lists the average Math Score for 
#students of each grade level (9th, 10th, 11th, 12th) at EACH SCHOOL.
grade_summary = merge_table.groupby(['school', 'grade'])
grade_summary.head()
grade_summary["math_score"].mean()
grade_summary_math = grade_summary["math_score"].mean()
grade_summary_math
#school = [merge_table['school']]
#grade = [merge_table['grade']]
#grade_math_summary_table = pd.DataFrame({"School": school,
#                                         "Grade":grade,
#                                         
#                              
#                             })
#grade_math_summary_table
```




    school                 grade
    Bailey High School     10th     76.996772
                           11th     77.515588
                           12th     76.492218
                           9th      77.083676
    Cabrera High School    10th     83.154506
                           11th     82.765560
                           12th     83.277487
                           9th      83.094697
    Figueroa High School   10th     76.539974
                           11th     76.884344
                           12th     77.151369
                           9th      76.403037
    Ford High School       10th     77.672316
                           11th     76.918058
                           12th     76.179963
                           9th      77.361345
    Griffin High School    10th     84.229064
                           11th     83.842105
                           12th     83.356164
                           9th      82.044010
    Hernandez High School  10th     77.337408
                           11th     77.136029
                           12th     77.186567
                           9th      77.438495
    Holden High School     10th     83.429825
                           11th     85.000000
                           12th     82.855422
                           9th      83.787402
    Huang High School      10th     75.908735
                           11th     76.446602
                           12th     77.225641
                           9th      77.027251
    Johnson High School    10th     76.691117
                           11th     77.491653
                           12th     76.863248
                           9th      77.187857
    Pena High School       10th     83.372000
                           11th     84.328125
                           12th     84.121547
                           9th      83.625455
    Rodriguez High School  10th     76.612500
                           11th     76.395626
                           12th     77.690748
                           9th      76.859966
    Shelton High School    10th     82.917411
                           11th     83.383495
                           12th     83.778976
                           9th      83.420755
    Thomas High School     10th     83.087886
                           11th     83.498795
                           12th     83.497041
                           9th      83.590022
    Wilson High School     10th     83.724422
                           11th     83.195326
                           12th     83.035794
                           9th      83.085578
    Wright High School     10th     84.010288
                           11th     83.836782
                           12th     83.644986
                           9th      83.264706
    Name: math_score, dtype: float64




```python
#Reading Scores by Grade
#Create a table that lists the average Reading Score 
#for students of each grade level (9th, 10th, 11th, 12th) at EACH SCHOOL.
grade_summary = merge_table.groupby(['school', 'grade'])
grade_summary.head()
grade_summary["reading_score"].mean()
grade_summary_reading = grade_summary["reading_score"].mean()
grade_summary_reading
```




    school                 grade
    Bailey High School     10th     80.907183
                           11th     80.945643
                           12th     80.912451
                           9th      81.303155
    Cabrera High School    10th     84.253219
                           11th     83.788382
                           12th     84.287958
                           9th      83.676136
    Figueroa High School   10th     81.408912
                           11th     80.640339
                           12th     81.384863
                           9th      81.198598
    Ford High School       10th     81.262712
                           11th     80.403642
                           12th     80.662338
                           9th      80.632653
    Griffin High School    10th     83.706897
                           11th     84.288089
                           12th     84.013699
                           9th      83.369193
    Hernandez High School  10th     80.660147
                           11th     81.396140
                           12th     80.857143
                           9th      80.866860
    Holden High School     10th     83.324561
                           11th     83.815534
                           12th     84.698795
                           9th      83.677165
    Huang High School      10th     81.512386
                           11th     81.417476
                           12th     80.305983
                           9th      81.290284
    Johnson High School    10th     80.773431
                           11th     80.616027
                           12th     81.227564
                           9th      81.260714
    Pena High School       10th     83.612000
                           11th     84.335938
                           12th     84.591160
                           9th      83.807273
    Rodriguez High School  10th     80.629808
                           11th     80.864811
                           12th     80.376426
                           9th      80.993127
    Shelton High School    10th     83.441964
                           11th     84.373786
                           12th     82.781671
                           9th      84.122642
    Thomas High School     10th     84.254157
                           11th     83.585542
                           12th     83.831361
                           9th      83.728850
    Wilson High School     10th     84.021452
                           11th     83.764608
                           12th     84.317673
                           9th      83.939778
    Wright High School     10th     83.812757
                           11th     84.156322
                           12th     84.073171
                           9th      83.833333
    Name: reading_score, dtype: float64




```python
#Scores by School Spending
#Create a table that breaks down school performances based on average Spending Ranges (Per Student). 
#Use 4 reasonable bins to group school spending. Include in the table each of the following:

school_performance = merge_table.loc[: ,["school","math_score_mean", "reading_score_mean","budget"]]
school_performance
school_performance["math_score_mean"] = merge_table['math_score']
school_performance["reading_score_mean"] = merge_table['reading_score']
school_performance["per_student_budget"] = school_performance["budget"]/total_students
school_performance["school_budget"] = school_performance["budget"]

bins = [0, 1000000, 2000000, 3000000, 4000000]

# Create the names for the four bins
group_names = ['low', 'midlow', 'midhigh', 'high']
school_performance
school_performance["SizeBins"] = pd.cut(school_performance["budget"], bins, labels=group_names)
school_performance.head()
school_performance = school_performance.groupby("SizeBins")
school_performance.mean()
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
      <th>math_score_mean</th>
      <th>reading_score_mean</th>
      <th>budget</th>
      <th>per_student_budget</th>
      <th>school_budget</th>
    </tr>
    <tr>
      <th>SizeBins</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>low</th>
      <td>83.583479</td>
      <td>83.893245</td>
      <td>7.057818e+05</td>
      <td>18.018427</td>
      <td>7.057818e+05</td>
    </tr>
    <tr>
      <th>midlow</th>
      <td>80.213577</td>
      <td>82.529094</td>
      <td>1.473563e+06</td>
      <td>37.619692</td>
      <td>1.473563e+06</td>
    </tr>
    <tr>
      <th>midhigh</th>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>2.547363e+06</td>
      <td>65.033521</td>
      <td>2.547363e+06</td>
    </tr>
    <tr>
      <th>high</th>
      <td>77.134219</td>
      <td>80.979474</td>
      <td>3.081710e+06</td>
      <td>78.675256</td>
      <td>3.081710e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Scores by School Size
#Repeat the above breakdown, but this time 
#group schools based on a reasonable approximation of school size (Small, Medium, Large).
school_performance = merge_table.loc[:,["size"]]
school_performance
total_students = merge_table["Student ID"].count()
total_students
bins = [0, 1000, 3000, 5000]
total_students
school_performance["math_score_mean"] = merge_table['math_score']
school_performance["reading_score_mean"] = merge_table['reading_score']

# Create the names for the four bins
schoolsize = ['Small', 'Medium', 'Large']
school_performance
school_performance["School Size"] = pd.cut(school_performance["size"], bins, labels=schoolsize)

school_performance = school_performance.groupby("School Size")
school_performance.mean()
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
      <th>size</th>
      <th>math_score_mean</th>
      <th>reading_score_mean</th>
    </tr>
    <tr>
      <th>School Size</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small</th>
      <td>797.532757</td>
      <td>83.828654</td>
      <td>83.974082</td>
    </tr>
    <tr>
      <th>Medium</th>
      <td>2294.757032</td>
      <td>80.450902</td>
      <td>82.626481</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>4621.573295</td>
      <td>77.070764</td>
      <td>80.928365</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Scores by School Type
#Repeat the above breakdown, but this time 
#group schools based on school type (Charter vs. District).
school_performance = merge_table.loc[: ,["type","size"]]
total_students = merge_table["Student ID"].count()
total_schools = merge_table["school"].count()
school_performance["average_math_score"] = merge_table['math_score']
school_performance["average_reading_score"] = merge_table['reading_score']

school_performance = school_performance.groupby("type")
school_performance.mean()
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
      <th>size</th>
      <th>average_math_score</th>
      <th>average_reading_score</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>1717.352468</td>
      <td>83.406183</td>
      <td>83.902821</td>
    </tr>
    <tr>
      <th>District</th>
      <td>4063.261195</td>
      <td>76.987026</td>
      <td>80.962485</td>
    </tr>
  </tbody>
</table>
</div>



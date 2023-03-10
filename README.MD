# Several methods to split a pandas DataFrame/Series

```python
pip install a-pandas-ex-split
```

```python


from a_pandas_ex_split import pd_add_df_split
import pandas as pd
pd_add_df_split()

df = pd.read_csv(
    "https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/titanic.csv"
)
df = df[:50]
t1 = df.ds_iloc_split(splitindex=[10, 20, 40])
print(f"\n\n{t1=}")
t2 = df.ds_loc_split(splitindex=[10, 20, 35])
print(f"\n\n{t2=}")
t3 = df.ds_iloc_split_pairwise(splitindex=[(0, 10), (25, 30)], include_last=True)
print(f"\n\n{t3=}")
t4 = df.ds_split_in_n_parts(n=9)  # len of results = [6, 6, 6, 6, 6, 5, 5, 5, 5]
print(f"\n\n{t4=}")
t5 = df.ds_split_in_n_parts_of_length(
    size_of_each=8, exact_split=False
)  # len of results = [9, 9, 8, 8, 8, 8]
print(f"\n\n{t5=}")
t6 = df.ds_split_in_n_parts_of_length(
    size_of_each=8, exact_split=True
)  # len of results = [8, 8, 8, 8, 8, 8, 2]
print(f"\n\n{t6=}")

t7 = df.PassengerId.ds_split_in_n_parts_of_length(
    size_of_each=8, exact_split=True
)  # len of results = [8, 8, 8, 8, 8, 8, 2]
print(f"\n\n{t7=}")





t1=[   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0            1         0       3  ...   7.2500   NaN         S
1            2         1       1  ...  71.2833   C85         C
2            3         1       3  ...   7.9250   NaN         S
3            4         1       1  ...  53.1000  C123         S
4            5         0       3  ...   8.0500   NaN         S
5            6         0       3  ...   8.4583   NaN         Q
6            7         0       1  ...  51.8625   E46         S
7            8         0       3  ...  21.0750   NaN         S
8            9         1       3  ...  11.1333   NaN         S
9           10         1       2  ...  30.0708   NaN         C
[10 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
10           11         1       3  ...  16.7000    G6         S
11           12         1       1  ...  26.5500  C103         S
12           13         0       3  ...   8.0500   NaN         S
13           14         0       3  ...  31.2750   NaN         S
14           15         0       3  ...   7.8542   NaN         S
15           16         1       2  ...  16.0000   NaN         S
16           17         0       3  ...  29.1250   NaN         Q
17           18         1       2  ...  13.0000   NaN         S
18           19         0       3  ...  18.0000   NaN         S
19           20         1       3  ...   7.2250   NaN         C
[10 rows x 12 columns],     PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
20           21         0       2  ...   26.0000          NaN         S
21           22         1       2  ...   13.0000          D56         S
22           23         1       3  ...    8.0292          NaN         Q
23           24         1       1  ...   35.5000           A6         S
24           25         0       3  ...   21.0750          NaN         S
25           26         1       3  ...   31.3875          NaN         S
26           27         0       3  ...    7.2250          NaN         C
27           28         0       1  ...  263.0000  C23 C25 C27         S
28           29         1       3  ...    7.8792          NaN         Q
29           30         0       3  ...    7.8958          NaN         S
30           31         0       1  ...   27.7208          NaN         C
31           32         1       1  ...  146.5208          B78         C
32           33         1       3  ...    7.7500          NaN         Q
33           34         0       2  ...   10.5000          NaN         S
34           35         0       1  ...   82.1708          NaN         C
35           36         0       1  ...   52.0000          NaN         S
36           37         1       3  ...    7.2292          NaN         C
37           38         0       3  ...    8.0500          NaN         S
38           39         0       3  ...   18.0000          NaN         S
39           40         1       3  ...   11.2417          NaN         C
[20 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
40           41         0       3  ...   9.4750   NaN         S
41           42         0       2  ...  21.0000   NaN         S
42           43         0       3  ...   7.8958   NaN         C
43           44         1       2  ...  41.5792   NaN         C
44           45         1       3  ...   7.8792   NaN         Q
45           46         0       3  ...   8.0500   NaN         S
46           47         0       3  ...  15.5000   NaN         Q
47           48         1       3  ...   7.7500   NaN         Q
48           49         0       3  ...  21.6792   NaN         C
49           50         0       3  ...  17.8000   NaN         S
[10 rows x 12 columns]]
t2=[    PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0             1         0       3  ...   7.2500   NaN         S
1             2         1       1  ...  71.2833   C85         C
2             3         1       3  ...   7.9250   NaN         S
3             4         1       1  ...  53.1000  C123         S
4             5         0       3  ...   8.0500   NaN         S
5             6         0       3  ...   8.4583   NaN         Q
6             7         0       1  ...  51.8625   E46         S
7             8         0       3  ...  21.0750   NaN         S
8             9         1       3  ...  11.1333   NaN         S
9            10         1       2  ...  30.0708   NaN         C
10           11         1       3  ...  16.7000    G6         S
[11 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
10           11         1       3  ...  16.7000    G6         S
11           12         1       1  ...  26.5500  C103         S
12           13         0       3  ...   8.0500   NaN         S
13           14         0       3  ...  31.2750   NaN         S
14           15         0       3  ...   7.8542   NaN         S
15           16         1       2  ...  16.0000   NaN         S
16           17         0       3  ...  29.1250   NaN         Q
17           18         1       2  ...  13.0000   NaN         S
18           19         0       3  ...  18.0000   NaN         S
19           20         1       3  ...   7.2250   NaN         C
20           21         0       2  ...  26.0000   NaN         S
[11 rows x 12 columns],     PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
20           21         0       2  ...   26.0000          NaN         S
21           22         1       2  ...   13.0000          D56         S
22           23         1       3  ...    8.0292          NaN         Q
23           24         1       1  ...   35.5000           A6         S
24           25         0       3  ...   21.0750          NaN         S
25           26         1       3  ...   31.3875          NaN         S
26           27         0       3  ...    7.2250          NaN         C
27           28         0       1  ...  263.0000  C23 C25 C27         S
28           29         1       3  ...    7.8792          NaN         Q
29           30         0       3  ...    7.8958          NaN         S
30           31         0       1  ...   27.7208          NaN         C
31           32         1       1  ...  146.5208          B78         C
32           33         1       3  ...    7.7500          NaN         Q
33           34         0       2  ...   10.5000          NaN         S
34           35         0       1  ...   82.1708          NaN         C
35           36         0       1  ...   52.0000          NaN         S
[16 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
35           36         0       1  ...  52.0000   NaN         S
36           37         1       3  ...   7.2292   NaN         C
37           38         0       3  ...   8.0500   NaN         S
38           39         0       3  ...  18.0000   NaN         S
39           40         1       3  ...  11.2417   NaN         C
40           41         0       3  ...   9.4750   NaN         S
41           42         0       2  ...  21.0000   NaN         S
42           43         0       3  ...   7.8958   NaN         C
43           44         1       2  ...  41.5792   NaN         C
44           45         1       3  ...   7.8792   NaN         Q
45           46         0       3  ...   8.0500   NaN         S
46           47         0       3  ...  15.5000   NaN         Q
47           48         1       3  ...   7.7500   NaN         Q
48           49         0       3  ...  21.6792   NaN         C
49           50         0       3  ...  17.8000   NaN         S
[15 rows x 12 columns]]
t3=[    PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0             1         0       3  ...   7.2500   NaN         S
1             2         1       1  ...  71.2833   C85         C
2             3         1       3  ...   7.9250   NaN         S
3             4         1       1  ...  53.1000  C123         S
4             5         0       3  ...   8.0500   NaN         S
5             6         0       3  ...   8.4583   NaN         Q
6             7         0       1  ...  51.8625   E46         S
7             8         0       3  ...  21.0750   NaN         S
8             9         1       3  ...  11.1333   NaN         S
9            10         1       2  ...  30.0708   NaN         C
10           11         1       3  ...  16.7000    G6         S
[11 rows x 12 columns],     PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
25           26         1       3  ...   31.3875          NaN         S
26           27         0       3  ...    7.2250          NaN         C
27           28         0       1  ...  263.0000  C23 C25 C27         S
28           29         1       3  ...    7.8792          NaN         Q
29           30         0       3  ...    7.8958          NaN         S
30           31         0       1  ...   27.7208          NaN         C
[6 rows x 12 columns]]
t4=[   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0            1         0       3  ...   7.2500   NaN         S
1            2         1       1  ...  71.2833   C85         C
2            3         1       3  ...   7.9250   NaN         S
3            4         1       1  ...  53.1000  C123         S
4            5         0       3  ...   8.0500   NaN         S
5            6         0       3  ...   8.4583   NaN         Q
[6 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
6             7         0       1  ...  51.8625   E46         S
7             8         0       3  ...  21.0750   NaN         S
8             9         1       3  ...  11.1333   NaN         S
9            10         1       2  ...  30.0708   NaN         C
10           11         1       3  ...  16.7000    G6         S
11           12         1       1  ...  26.5500  C103         S
[6 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
12           13         0       3  ...   8.0500   NaN         S
13           14         0       3  ...  31.2750   NaN         S
14           15         0       3  ...   7.8542   NaN         S
15           16         1       2  ...  16.0000   NaN         S
16           17         0       3  ...  29.1250   NaN         Q
17           18         1       2  ...  13.0000   NaN         S
[6 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
18           19         0       3  ...  18.0000   NaN         S
19           20         1       3  ...   7.2250   NaN         C
20           21         0       2  ...  26.0000   NaN         S
21           22         1       2  ...  13.0000   D56         S
22           23         1       3  ...   8.0292   NaN         Q
23           24         1       1  ...  35.5000    A6         S
[6 rows x 12 columns],     PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
24           25         0       3  ...   21.0750          NaN         S
25           26         1       3  ...   31.3875          NaN         S
26           27         0       3  ...    7.2250          NaN         C
27           28         0       1  ...  263.0000  C23 C25 C27         S
28           29         1       3  ...    7.8792          NaN         Q
29           30         0       3  ...    7.8958          NaN         S
[6 rows x 12 columns],     PassengerId  Survived  Pclass  ...      Fare Cabin  Embarked
30           31         0       1  ...   27.7208   NaN         C
31           32         1       1  ...  146.5208   B78         C
32           33         1       3  ...    7.7500   NaN         Q
33           34         0       2  ...   10.5000   NaN         S
34           35         0       1  ...   82.1708   NaN         C
[5 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
35           36         0       1  ...  52.0000   NaN         S
36           37         1       3  ...   7.2292   NaN         C
37           38         0       3  ...   8.0500   NaN         S
38           39         0       3  ...  18.0000   NaN         S
39           40         1       3  ...  11.2417   NaN         C
[5 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
40           41         0       3  ...   9.4750   NaN         S
41           42         0       2  ...  21.0000   NaN         S
42           43         0       3  ...   7.8958   NaN         C
43           44         1       2  ...  41.5792   NaN         C
44           45         1       3  ...   7.8792   NaN         Q
[5 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
45           46         0       3  ...   8.0500   NaN         S
46           47         0       3  ...  15.5000   NaN         Q
47           48         1       3  ...   7.7500   NaN         Q
48           49         0       3  ...  21.6792   NaN         C
49           50         0       3  ...  17.8000   NaN         S
[5 rows x 12 columns]]
t5=[   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0            1         0       3  ...   7.2500   NaN         S
1            2         1       1  ...  71.2833   C85         C
2            3         1       3  ...   7.9250   NaN         S
3            4         1       1  ...  53.1000  C123         S
4            5         0       3  ...   8.0500   NaN         S
5            6         0       3  ...   8.4583   NaN         Q
6            7         0       1  ...  51.8625   E46         S
7            8         0       3  ...  21.0750   NaN         S
8            9         1       3  ...  11.1333   NaN         S
[9 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
9            10         1       2  ...  30.0708   NaN         C
10           11         1       3  ...  16.7000    G6         S
11           12         1       1  ...  26.5500  C103         S
12           13         0       3  ...   8.0500   NaN         S
13           14         0       3  ...  31.2750   NaN         S
14           15         0       3  ...   7.8542   NaN         S
15           16         1       2  ...  16.0000   NaN         S
16           17         0       3  ...  29.1250   NaN         Q
17           18         1       2  ...  13.0000   NaN         S
[9 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
18           19         0       3  ...  18.0000   NaN         S
19           20         1       3  ...   7.2250   NaN         C
20           21         0       2  ...  26.0000   NaN         S
21           22         1       2  ...  13.0000   D56         S
22           23         1       3  ...   8.0292   NaN         Q
23           24         1       1  ...  35.5000    A6         S
24           25         0       3  ...  21.0750   NaN         S
25           26         1       3  ...  31.3875   NaN         S
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
26           27         0       3  ...    7.2250          NaN         C
27           28         0       1  ...  263.0000  C23 C25 C27         S
28           29         1       3  ...    7.8792          NaN         Q
29           30         0       3  ...    7.8958          NaN         S
30           31         0       1  ...   27.7208          NaN         C
31           32         1       1  ...  146.5208          B78         C
32           33         1       3  ...    7.7500          NaN         Q
33           34         0       2  ...   10.5000          NaN         S
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
34           35         0       1  ...  82.1708   NaN         C
35           36         0       1  ...  52.0000   NaN         S
36           37         1       3  ...   7.2292   NaN         C
37           38         0       3  ...   8.0500   NaN         S
38           39         0       3  ...  18.0000   NaN         S
39           40         1       3  ...  11.2417   NaN         C
40           41         0       3  ...   9.4750   NaN         S
41           42         0       2  ...  21.0000   NaN         S
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
42           43         0       3  ...   7.8958   NaN         C
43           44         1       2  ...  41.5792   NaN         C
44           45         1       3  ...   7.8792   NaN         Q
45           46         0       3  ...   8.0500   NaN         S
46           47         0       3  ...  15.5000   NaN         Q
47           48         1       3  ...   7.7500   NaN         Q
48           49         0       3  ...  21.6792   NaN         C
49           50         0       3  ...  17.8000   NaN         S
[8 rows x 12 columns]]
t6=[   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0            1         0       3  ...   7.2500   NaN         S
1            2         1       1  ...  71.2833   C85         C
2            3         1       3  ...   7.9250   NaN         S
3            4         1       1  ...  53.1000  C123         S
4            5         0       3  ...   8.0500   NaN         S
5            6         0       3  ...   8.4583   NaN         Q
6            7         0       1  ...  51.8625   E46         S
7            8         0       3  ...  21.0750   NaN         S
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
8             9         1       3  ...  11.1333   NaN         S
9            10         1       2  ...  30.0708   NaN         C
10           11         1       3  ...  16.7000    G6         S
11           12         1       1  ...  26.5500  C103         S
12           13         0       3  ...   8.0500   NaN         S
13           14         0       3  ...  31.2750   NaN         S
14           15         0       3  ...   7.8542   NaN         S
15           16         1       2  ...  16.0000   NaN         S
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
16           17         0       3  ...  29.1250   NaN         Q
17           18         1       2  ...  13.0000   NaN         S
18           19         0       3  ...  18.0000   NaN         S
19           20         1       3  ...   7.2250   NaN         C
20           21         0       2  ...  26.0000   NaN         S
21           22         1       2  ...  13.0000   D56         S
22           23         1       3  ...   8.0292   NaN         Q
23           24         1       1  ...  35.5000    A6         S
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
24           25         0       3  ...   21.0750          NaN         S
25           26         1       3  ...   31.3875          NaN         S
26           27         0       3  ...    7.2250          NaN         C
27           28         0       1  ...  263.0000  C23 C25 C27         S
28           29         1       3  ...    7.8792          NaN         Q
29           30         0       3  ...    7.8958          NaN         S
30           31         0       1  ...   27.7208          NaN         C
31           32         1       1  ...  146.5208          B78         C
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
32           33         1       3  ...   7.7500   NaN         Q
33           34         0       2  ...  10.5000   NaN         S
34           35         0       1  ...  82.1708   NaN         C
35           36         0       1  ...  52.0000   NaN         S
36           37         1       3  ...   7.2292   NaN         C
37           38         0       3  ...   8.0500   NaN         S
38           39         0       3  ...  18.0000   NaN         S
39           40         1       3  ...  11.2417   NaN         C
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
40           41         0       3  ...   9.4750   NaN         S
41           42         0       2  ...  21.0000   NaN         S
42           43         0       3  ...   7.8958   NaN         C
43           44         1       2  ...  41.5792   NaN         C
44           45         1       3  ...   7.8792   NaN         Q
45           46         0       3  ...   8.0500   NaN         S
46           47         0       3  ...  15.5000   NaN         Q
47           48         1       3  ...   7.7500   NaN         Q
[8 rows x 12 columns],     PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
48           49         0       3  ...  21.6792   NaN         C
49           50         0       3  ...  17.8000   NaN         S
[2 rows x 12 columns]]
t7=[0    1
1    2
2    3
3    4
4    5
5    6
6    7
7    8
Name: PassengerId, dtype: int64, 8      9
9     10
10    11
11    12
12    13
13    14
14    15
15    16
Name: PassengerId, dtype: int64, 16    17
17    18
18    19
19    20
20    21
21    22
22    23
23    24
Name: PassengerId, dtype: int64, 24    25
25    26
26    27
27    28
28    29
29    30
30    31
31    32
Name: PassengerId, dtype: int64, 32    33
33    34
34    35
35    36
36    37
37    38
38    39
39    40
Name: PassengerId, dtype: int64, 40    41
41    42
42    43
43    44
44    45
45    46
46    47
47    48
Name: PassengerId, dtype: int64, 48    49
49    50
Name: PassengerId, dtype: int64]


```

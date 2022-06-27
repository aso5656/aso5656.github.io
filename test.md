```python
#split long_text by delimeter \n to a list
long_text_to_list = [item for item in long_text.split("\n") if item] 

#helper function to return slice of long_text_to_list
def chunks(start,end):
    return long_text_to_list[start:end]

#create a new dict
data = dict()
data["name"] = long_text_to_list [0]
data["lei"] = long_text_to_list [1]
subs = long_text_to_list[2:] #sub funds
#is a fund title if a string starts with a number 
subfunds_title = [item for item in subs if item[0].isnumeric() ] 
#['1. TARENO GLOBAL WATER SOLUTIONS FUND',
# '2. TARENO FIXED INCOME FUND',
# '3. TARENO GLOBAL EQUITY FUND',
# '4. MIV GLOBAL MEDTECH FUND']

#create sub_fund value
subfunds=[dict([("title",item[item.find(".")+2 : ]),("isin",[])])for item in subfunds_title]
#[{'title': 'TARENO GLOBAL WATER SOLUTIONS FUND',
# 'isin': ['LU2001709034', 'LU2057889995', 'LU2001709547']},
#{'title': 'TARENO FIXED INCOME FUND', 'isin': ['LU1299722972']},
# {'title': 'TARENO GLOBAL EQUITY FUND',
# 'isin': ['LU1299721909', 'LU1299722113', 'LU1299722030']},
# {'title': 'MIV GLOBAL MEDTECH FUND',
# 'isin': ['LU0329630999', 'LU0329630130']}]

#Count values by index difference
sub_index = [subs.index(item) for item in subs]
sub_index.append(len(a))
#[0, 4, 6, 10, 13]

#slice the long_text_to_list
for i in range(len(sub_index)-1):
  #eg chunks(1,4) chunks(5,6)
  subfunds[i]["isin"]=chunks(sub_index [i]+1, sub_index [i+1])

data['sub_fund'] = subfunds

```

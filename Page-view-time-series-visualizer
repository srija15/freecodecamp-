# In[2]:


import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


# In[3]:


from urllib.request import urlretrieve


# In[4]:


data_df=r"C:\Users\kavya\Downloads\fcc-forum-pageviews (2).csv"


# In[5]:


data_df = pd.read_csv(r"C:\Users\kavya\Downloads\fcc-forum-pageviews (2).csv")


# In[6]:


data_df

#Use Pandas to import the data from "fcc-forum-pageviews.csv". Set the index to the date column.
# In[7]:


data_df = pd.read_csv(r'C:\Users\kavya\Downloads\fcc-forum-pageviews (2).csv', parse_dates= ['date'])
data_df = data_df.set_index(['date'])
data_df

Clean the data by filtering out days when the page views were in the top 2.5% of the dataset or bottom 2.5% of the dataset.
# In[8]:


bottom = int(data_df.quantile(q=.025))
top = int(data_df.quantile(q=.975))
top, bottom


# In[9]:


top_data =data_df[data_df['value'] >= top]
bottom_data =data_df[data_df['value'] <= bottom]
len(top_data), len(bottom_data)


# In[10]:


cleaned_data =data_df[(data_df['value'] < top) & (data_df['value'] > bottom)]
cleaned_data


# In[11]:


x = cleaned_data.index
y = cleaned_data['value']
def draw_line_plot():
    fig, ax = plt.subplots(figsize = (15,5))
    ax.plot(x,y,color='r',linewidth = 1.5)
    ax.set(title = "Daily freeCodeCamp Forum Page Views 5/2016-12/2019", xlabel = "Date", ylabel = "Page Views")
    fig.savefig('line_plot.png')
    return fig


# In[12]:


fig, ax = plt.subplots(figsize = (15,5))
ax.plot(x,y, color = 'red', linewidth = 1.5)
ax.set(title = "Daily freeCodeCamp Forum Page Views 5/2016-12/2019", xlabel = "Date", ylabel = "Page Views")
fig.savefig('line_plot.png')


# In[13]:


data_2016_to_2019 = data_df.groupby([data_df.index.strftime('%Y-%m')])['value'].mean().reset_index(name = 'Average Page Views')
data_2016_to_2019_month = []
data_2016_to_2019_views =  []
for i in data_2016_to_2019['date']:
    data_2016_to_2019_month.append(i)
for j in data_2016_to_2019['Average Page Views']:
    data_2016_to_2019_views.append(j)

data_2016_to_2019_dict = dict(zip(data_2016_to_2019_month,data_2016_to_2019_views))

data_2016_list = []
for i in range (0,4):
    data_2016_list.append(0)
data_2017_list = []
data_2018_list = []
data_2019_list = []
for i in data_2016_to_2019['date']:
    if '2016' in i:
        data_2016_list.append(i)
for i in data_2016_to_2019['date']:
    if '2017' in i:
        data_2017_list.append(i)
for i in data_2016_to_2019['date']:
    if '2018' in i:
        data_2018_list.append(i)
for i in data_2016_to_2019['date']:
    if '2019' in i:
        data_2019_list.append(i)
data_2016_list, data_2017_list, data_2018_list, data_2019_list


# In[14]:


data_2016_views_list = []
for i in range(0,4):
    data_2016_views_list.append(0)
data_2017_views_list = []
data_2018_views_list = []
data_2019_views_list = []
for i in data_2016_to_2019_dict.keys():
    if '2016' in i:
        data_2016_views_list.append(data_2016_to_2019_dict.get(i))
    elif '2017' in i:
        data_2017_views_list.append(data_2016_to_2019_dict.get(i))
    elif '2018' in i:
        data_2018_views_list.append(data_2016_to_2019_dict.get(i))
    elif '2019' in i:
        data_2019_views_list.append(data_2016_to_2019_dict.get(i))
data_2016_views_list, data_2017_views_list, data_2018_views_list, data_2019_views_list


# In[15]:


year = ['2017','2018','2019']
views = [data_2017_views_list,data_2018_views_list,data_2019_views_list]
dict_views_2017_to_2019 = dict(zip(year,views))
data_df_views_2017_to_2019 = pd.DataFrame(dict_views_2017_to_2019)
data_df_views_2016 = pd.DataFrame({'2016' : data_2016_views_list})
data_df_views_new = pd.concat([data_df_views_2016,data_df_views_2017_to_2019], axis = 1)
data_df_views_new['2016'] = data_df_views_new['2016'].fillna(0) 
data_df_views_new['months'] = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
data_df_views_final = data_df_views_new.set_index('months')
data_df_views_final.T


# In[16]:


data_df_views_final.T.plot.bar(figsize = (15,10), xlabel = "Years", ylabel = "Average Page Views")
plt.show()


# In[17]:


def draw_bar_plot():
    data_df_bar = data_df_views_final.T
    data_df_bar.plot.bar(figsize = (15,10), xlabel = "Years", ylabel = "Average Page Views")
    fig.savefig('bar_plot.png')
    return fig


# In[18]:


data_df_box = data_df.copy()
data_df_box.reset_index(inplace=True)
data_df_box['year'] = [d.year for d in data_df_box.date]
data_df_box['month'] = [d.strftime('%b') for d in data_df_box.date]
data_df_box


# In[19]:


sns.set(rc={"figure.figsize":(15,20)})
sns.boxplot(x=data_df_box['year'], y = data_df_box['value']).set(xlabel = "Year", ylabel = "Page Views", title = "Year-wise Box Plot (Trend)")

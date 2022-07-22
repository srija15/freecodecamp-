import numpy as np 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


# In[5]:


from urllib.request import urlretrieve


# In[17]:


data=r'C:\Users\kavya\Downloads\ad.csv'


# In[12]:


data_df = pd.read_csv(r"C:\Users\kavya\Downloads\ad.csv")


# In[18]:


data_df


# In[25]:


#How many people of each race are represented in this dataset? This should be a Pandas series with race names as the index labels
race_count =data_df.groupby('race')
race_count['race'].count()


# In[42]:


#How many people of each race are represented in this dataset? This should be a Pandas series with race names as the index labels
race_count =data_df.groupby('education')
race_count['education'].count()


# In[26]:


# What is the average age of men?
average_age_men =data_df[data_df['sex'] == 'Male']['age'].mean()


# In[27]:


average_age_men


# In[47]:


#What is the percentage of people who have a Bachelor's degree?
percentage_bachelor=data_df[data_df['education']=='Bachelors'].shape[0]/data_df.shape[0]*100


# In[48]:


percentage_bachelor


# In[52]:


#What percentage of people with advanced education (Bachelors, Masters, or Doctorate) make more than 50K?
higher_education =data_df[data_df['education'].isin(['Bachelors', 'Masters', 'Doctorate'])]
lower_education =data_df[~data_df['education'].isin(['Bachelors', 'Masters', 'Doctorate'])]


# In[53]:


higher_education


# In[55]:



lower_education


# In[58]:


higher_education_rich = higher_education[higher_education['income'] == '>50K']['income'].count() / higher_education.shape[0] * 100


# In[59]:


higher_education_rich


# In[60]:


#What percentage of people without advanced education make more than 50K?
lower_education_rich = lower_education[lower_education['income'] == '>50K']['income'].count() / lower_education.shape[0] * 100


# In[61]:


lower_education_rich


# In[64]:


#What is the minimum number of hours a person works per week?
min_work_hours =data_df['hours.per.week'].min()


# In[65]:


min_work_hours


# In[66]:


max_work_hours =data_df['hours.per.week'].max()


# In[68]:


max_work_hours


# In[72]:


#What percentage of the people who work the minimum number of hours per week have a salary of more than 50K?
num_min_workers =data_df[data_df['hours.per.week'] == 1]['hours.per.week'].count()


# In[73]:


num_min_workers


# In[74]:


rich_percentage =data_df[(data_df['hours.per.week'] == 1) & (data_df['income'] == '>50K')].shape[0] / num_min_workers


# In[75]:


rich_percentage


# In[78]:


#What country has the highest percentage of people that earn >50K and what is that percentage?
highest_earning_country =data_df[data_df['income'] == '>50K'].groupby('native.country')['native.country'].count().max()


# In[79]:


highest_earning_country


# In[87]:


# Identify the most popular occupation for those who earn >50K in India.
top_IN_occupation = data_df[(data_df['native.country'] == 'India') & (data_df['income'] == '>50K')].groupby('occupation')['occupation'].count().max()


# In[88]:


top_IN_occupation

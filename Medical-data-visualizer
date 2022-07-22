# In[1]:


import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


# In[2]:


from urllib.request import urlretrieve


# In[5]:


data_df = pd.read_csv(r"C:\Users\kavya\Downloads\med.csv")


# In[6]:


data_df

# Add an overweight column to the data. To determine if a person is overweight, first calculate their BMI by dividing their weight in kilograms by the square of their height in meters. If that value is > 25 then the person is overweight. Use the value 0 for NOT overweight and the value 1 for overweight.
# In[17]:


bmi = (data_df['weight']) / ((data_df['height'] / 100) ** 2)


# In[18]:


bmi


# In[19]:


data_df['overweight'] = [1 if value > 25 else 0 for value in bmi]


# In[20]:


data_df['overweight']

# Normalize the data by making 0 always good and 1 always bad. If the value of cholesterol or gluc is 1, make the value 0. If the value is more than 1, make the value 1.
# In[27]:


data_df['cholesterol']=[0 if value==1 else 1 for value in data_df['cholesterol']]


# In[28]:


data_df['cholesterol']


# In[29]:


data_df['gluc']=[0 if value==1 else 1 for value in data_df['gluc']]


# In[30]:


data_df['gluc']

# Convert the data into long format and create a chart that shows the value counts of the categorical features using seaborn's catplot(). The dataset should be split by 'Cardio' so there is one chart for each cardio value. 
# In[33]:


data_df_cat = pd.melt(data_df,id_vars=['cardio'],value_vars=['active', 'alco', 'cholesterol', 'gluc', 'overweight', 'smoke'])


# In[34]:


data_df_cat


# In[36]:


data_df_cat =data_df_cat.groupby(['cardio', 'variable', 'value']).size().rename('total').reset_index()
cat_plot = sns.catplot(data =data_df_cat, x = 'variable', y = 'total', kind = 'bar', hue = 'value', col = 'cardio')

Create a correlation matrix using the dataset. Plot the correlation matrix using seaborn's heatmap().
# In[42]:


data_df_heat =data_df[(data_df['ap_lo'] <= data_df['ap_hi']) &
(data_df['height'] >= data_df['height'].quantile(0.025)) &
(data_df['height'] <= data_df['height'].quantile(0.975)) &
(data_df['weight'] >= data_df['weight'].quantile(0.025)) &
(data_df['weight'] <= data_df['weight'].quantile(0.975)) ]


# In[47]:


data_df_heat


# In[ ]:


# Calculate the correlation matrix
corr = data_df_heat.corr()

# Generate a mask for the upper triangle
mask = np.zeros_like(corr, dtype=np.bool)
mask[np.triu_indices_from(mask)] = True

# Set up the matplotlib figure
fig, ax = plt.subplots(figsize=(10, 12))

# Draw the heatmap with the mask
sns.heatmap(corr, annot=True, fmt='.1f', mask=mask, vmin=.16, vmax=.32, center=0, square=True, linewidths=.5, cbar_kws={'shrink':.45, 'format':'%.2f'})


# In[ ]:

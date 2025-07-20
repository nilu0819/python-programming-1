# python-programming-1
#api integration and data visualization

#fetch data from the api
import requests
import pandas as pd

# Fetch posts from JSONPlaceholder
response = requests.get("https://jsonplaceholder.typicode.com/posts")
posts = response.json()

# Convert to DataFrame
df = pd.DataFrame(posts)

#analyze and prepare data

# Count number of posts per user
post_counts = df['userId'].value_counts().sort_index()
post_data = pd.DataFrame({'userId': post_counts.index, 'post_count': post_counts.values})

# visualize using seaborn
import seaborn as sns
import matplotlib.pyplot as plt

sns.set(style="whitegrid")

# Create barplot
plt.figure(figsize=(10, 6))
sns.barplot(x='userId', y='post_count', data=post_data, palette='viridis')

plt.title('Number of Posts per User')
plt.xlabel('User ID')
plt.ylabel('Post Count')
plt.show()


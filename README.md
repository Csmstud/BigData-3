# BigData-3
#importer ulike biblioteker som benyttes i koden
#bruker denne for å lese filen
from collections import Counter
import pandas as pd
from sklearn import neighbors
from matplotlib import pyplot as plt 
from io import StringIO
#navngir hvilken fil som skal leses
df = pd.read_csv('dishes.csv', sep=';')
#printer ut csv filen
print (df)


#kode for å lage diagram
labels, values = zip(*Counter(df['Dish'].values).items())
x = range(len(labels))
#henter gjennomsnitt score på dish
mean = df.groupby(['Dish']).mean()
labels = mean.index.values
values = mean['Score'].values
#printer diagrammet med størrelse
plt.figure(figsize=(20,10)) # Make the plot bigger
plt.bar(x, values, 0.6) # Create the plot with a little space between the bars
plt.xticks(x, labels)
plt.show()

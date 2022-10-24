# Ironhack Project 2
Bernat Bellmunt

## Best Sellers study

###Sources:
- CSV file that contains a register of historic titles classified as Best Sellers
- New York Times book API that contains the real-time Best Seller Rank

###Aim of my study:
- Discover relationship between the two pieces of data
- Relationship between rating and number of reviews
- Identify the most valued: title, author, publishers
- Title with the longer presence in NYT Best Seller list
- Most preffered genre

###Discover relationship between the two pieces of data
The data has a common identifier (ISBN). ISBN is a 13 digit object that identifies each book.
When looking for the actual bestsellers ISBN's in our database we obtain that none of the ISBN's are in our database. This could be due to our CSV contains older books, that are currently not as popular to the ones that appear in the NYT Rank.

```python 
lista= []
for id in df_bestsellernyt["isbn"]:
    if id in df_raw2["isbn"]:
        lista.append(id)
len(lista)
```
The length of this list is 0, meaning that no ISBN's are common.


###Relationship between rating and number of reviews
Are titles that are getting a higher number of reviews getting a better rating?
![](images/Screenshot%202022-10-24%20at%2011.17.10.png)

In the previous graph we can see that there is a positive tendency between the number of ratings and the rating value, therefore we can say that the more number of ratings a title has, the more probable is that the rating is higher.


###Identify the most valued: title, author, publishers
How can we measure value? We will look into both number of ratings and the rate value. We will create a new value (all_rate), that is the product of numRatings * rating
####Most valued titles (top 10):
![](images/Screenshot%202022-10-24%20at%2011.35.18.png)
####Most valued authors (top 10):
![](images/Screenshot%202022-10-24%20at%2011.37.03.png)
####Most valued publishers
For publishers, we will look into how many titles does each publisher has in our dataset, and in the NYT rank.

**Titles by Publisher in our dataset (Top 5):**
![](images/Screenshot%202022-10-24%20at%2011.32.04.png)

**Titles by Publisher in the current NYT Best Seller Rank (Top 5):**
![](images/Screenshot%202022-10-24%20at%2011.32.15.png)

We don't spot a clear relationship between the actual rank and our dataset.

###Titles with the longer presence in NYT Best Seller list
![](images/Screenshot%202022-10-24%20at%2011.50.19.png)

![](images/Screenshot%202022-10-24%20at%2011.56.18.png)

Observation: When looking for Harry Potter's ISBN code, the book is Order of The Phoenix, which appears in position 9 of the most valued titles from out DB.
Why won't they relate to each other? ISBN from our DB != ISBN from NYT.

##Most preffered genre
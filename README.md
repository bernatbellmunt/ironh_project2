# Ironhack Project 2
Bernat Bellmunt Cabutí

## Best Sellers study
![](images/200.gif)
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

###Most preffered genre

I will look into the genres now.
Our first piece of research is to know which is the most predominant genre in our dataset.

![](images/Screenshot%202022-10-24%20at%2015.43.14.png)

Fiction genre contains the highest number of books in our dataset. 
We should consider that in our original dataset, the genre column contained a list of various subgenres, I will just keep the first one to simplify.

Now we will look into the ratings of each rating. My goal is to identify which is the most well rated genre in average:

![](images/Screenshot%202022-10-24%20at%2015.43.40.png)

![](images/Screenshot%202022-10-24%20at%2015.43.30.png)


**Fantasy has the highest average rating in between all the genres.**

When looking at the book format, we can see that Paperback books are more sold by far, followed by the Hardback (traditional format). This might be like this as the Paperback is cheaper than Hardback. 

![](images/Screenshot%202022-10-24%20at%2015.58.47.png)


### Conclusions

After our analysis we can extract the following:

*Book format*

- Paperback format is the one that has the most overall titles as bestseller

*Genres*

- The genre with a higher number of best sellers is Fiction, however the genre prefered by the public (higher average rating) is Fantasy

*Publishers*

- In our database, the publisher that holds the larger number of best seller books is HarperCollins
- In the NYT Best Seller Rank the publisher that holds the larger number of titles in the current edition is Scholastic 

*Authors*

- The best ranked author in our database is Arthur Golden, writer of the well-known title Memoirs of a Geisha

*Titles*

- Our database identifies The Hunger Games, from Suzanne Collins as the most valued title, however, the title that has had the larger appereances in the NYT Best Seller Rank is Diary of a Wimpy Kid, written by Jeff Kinney, that has accumulated 709 total appereances, one more than JK Rowling's Harry Potter and the Order of the Phoenix.



![](images/giphy.gif)
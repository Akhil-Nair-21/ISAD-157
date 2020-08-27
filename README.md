# ISAD-157
Referral
Use ISAD157_ANair;
Create Table Users
( 
 UserId int Not Null Primary key,
 User_name varchar (15),      
 User_screenname varchar(15),
 User_created varchar (50)
);
Select*From Users;

Create Table tweets
(
TweetId int,
Texts varchar (150),
Tweet_created_at varchar (25),
UserID int,
User_screenname varchar (15),
User_name varchar (15),
Is_retweeted varchar (5),
Sources varchar (15),
Primary key (UserID, TweetId),
Foreign Key (UserID) References Users (UserId),
Foreign Key (User_Name) References Users (User_name),
Foreign Key (User_Screenname) References Users (User_screenname),
Foreign Key (TweetId) References Users (UserId)
);
Select*From tweets;

Create Table tweet_URL
(
TweetID int,
url varchar (15),
Primary Key (TweetID),
Foreign Key (TweetID) References tweets (TweetId)
);
Select*From tweet_URL;

Create Table tweet_hashtags
(
Tweetid int,
hashtags varchar (15),
Primary Key (Tweetid),
Foreign Key (Tweetid) References tweets (TweetId)
);
Select*From tweet_hashtags;

Select tweets.UserID, tweets.TweetId, User_name.tweets, User_screenname.tweets
From   
((tweets Inner Join Users On tweets.User_ID = Users.UserId,
tweets Inner Join Users On tweets.User_Name = Users.User_name,
tweets Inner Join Users On tweets.User_Screeaname = Users.User_screenname));

Select tweet_URL.TweetID
From 
((tweet_URL Inner Join tweets On tweet_URL.TweetID = tweets.TweetId));

Select tweet_hashtags.Tweetid
From
((tweet_hashtags Inner Join tweets On tweet_hashtags.Tweetid = tweets.TweetId));

Select*From Users;
Select*From tweets;
Select*From tweet_URL;
Select*From tweet_hashtags;

# Git Game
Welcome to WnCC's GitHub session
Let's play a little game set in a make belief world where 100 years after World War II, a time machine and an inefficient hashing algorithm were simultaneously built. Allow me to explain.
---

# The game
The scene is set in 1930, during the world war era. You are an army general and your country is up against Germany (I chose Germany at random). As the general, it is your job to send target cities to the battalion. However, there happens to be a German spy within your chain of command who intercepts your message and sends it to the Germans before hand, who are now prepared for an attack at the respective city. <br/>
Unprepared for such an interception, your army is caught off guard and you end up losing the war. <br/>
Fast forward 100 years. Your country is now under the rule of Germans. Filled with rage for your country and its people you end up developing a time machine. It is capable of travelling back in time and changing the messages that the general sent to the battalion.<br/>
There is a code that generates a hash value for a given string. In essence, it takes a word, Berlin for example, and converts it into a code that is generated using a function only you know about.<br/>
### Your mission, should you choose to accept it, is as follows:<br/>
- Clone the repositories from the WnCC repo<br/>
```git clone <http or ssh link>```
- You will find the git repository named ***world_war*** along with three c++ files, ***hashing.hpp***, ***hashing.cpp*** and ***main.cpp***.
- Change directory into the ```world_war``` repository
- Add the three .cpp files into world_war and commit the changes
- Create a new branch called ```hash_func```
- Edit the hash function generator codes as follows, to generate hash functions:<br/>
  Checkout into the ```hash_func``` branch
  In ***hashing.cpp*** implement polynomial hashing as follows: (add the line into the for loop)<br/>
  
  ```
  for(int i=0; i<s.length(); i++){
    sum=sum*p+s[i];
  }
  return sum%1000;
  ```
  add and commit these changes<br/>
  Meanwhile your partner in main is also working on the code and realises a possible overflow could occur in the code.<br/>
  To simulate this, checkout to main and do the following:<br/>
  ```
  for(int i=0; i<s.length(); i++){
    sum=(sum*p+s[i])%1000;
  }
  return sum;
  ```
  add and commit the changes<br/>
  Further, you realise that this hash function should generate numbers mod anything. So instead of 1000, you pass the number as a function parameter.
  Checkout to the hash_func branch and make the following change in ***hashing.cpp***
  ```
  int hash_string(string s, int m){
    int p=41;
    int sum=0;
    for(int i=0; i<s.length(); i++){
      sum=(sum*p+s[i])%m;
    }
    return sum;
  ```
  In ***hashing.hpp*** change the function signature to include an *int m* and in main.cpp pass 1000 to hash_string
  add and commit these changes<br/>
  It seems like we're done with the hash function.<br/>
  While you're in the hash_func branch, merge the main branch with your branch and resolve merge conflicts if any.<br/>
  Checkout to the master branch and merge the hash_func branch with masin<br/>
  Now run the hash generators:<br/>
  Either create a new folder and copy paste the three c++ files into it, or compile the codes in the current repository, create a .gitignore file and ignore all .out and .o files (bonus).<br/>
  Use:<br/>
  ```git log --graph --all```<br/>
  ```git log --graph --pretty="%s" --all```<br/>
  To see the commits and the city names<br/>
  To compile the code, in the directory that contains the files, run the following commands on your terminal<br/>
  ```g++ main.cpp```<br/>
  ```./a.out <city_name>```<br/>
  Behold! Your code<br/>
- Now all you have to do is go back in time and reset the commits to change the names of the cities into their corresponding hash values!<br/>
- Use git's interactive rebase to change all the city names and then fast forward back into the future<br/>
 Note: You will have to use ```git commit --amend``` to do this.
## You have officially rewritten history

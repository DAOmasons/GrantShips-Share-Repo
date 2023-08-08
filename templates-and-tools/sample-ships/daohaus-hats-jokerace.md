# 🏰 DAOhaus - Hats - Jokerace

### Tools needed for this Ship:

* DAOhaus DAOs
* Hats On-boarding Shaman
* Jokerace
  * Hats Joke Race Eligibility Module
* Discord

### How This Ship Floats

#### Easy DAO creation

DAOhaus provides a suite of tool to build custom DAO dApps. What is also really nice about the DAOhaus platform is they make it easy to summon a new DAO from within their summoners app. However don't let the ease of summoning fool you, DAOhaus is a powerful tool which uses the Moloch DAO v3 contracts providing an array of governance options.

DAOhaus v3 sits on top of Safe, using the Zodiac module, which allows for governance decisions made within the DAOhaus app, to manage the treasury including awarded grants from the ship.

#### Small DAOs DAOhaus Shines

The DAOhaus protocol certainly has the chops to perform alongside any DAO governance framework but it really shines when it comes to managing smaller teams. As Grant Ships is designed around small teams, DAOhaus is perfectly suited for this game.

#### DAOhaus Hats On-boarding Shaman

Hats Protocol has developed a "Shaman" contract which on-boards and off-boards members of a Moloch DAO based on if they are wearing a Hat or not. This is fits perfectly with our game as it will allow the game to remove or sideline players as needed.

You can check out the shaman [here](https://github.com/grantships/hats-baal-shamans).

#### Jokerace

Jokerace can be used in a couple different ways in this particular sample design.

The first case we can explore is voting for member to be in a grant ship, using jokerace. Jokerace will allow a number of different options for who can vote. Those logistics are not important to explain this design.

After the winner in the race are determined, the eligibility module can be called to automatically award the winners with their Hats. At this time, the DAOhaus On-boarding Shaman can be called and the newly minted Hats, will become a member of a DAOhaus DAO.

Jokerace can also serve a secondary role in this design. Which is to be the main voting mechanism for the actual grants. Applicants can post their grant applications to a jokerace and the winners awarded hats, which would allow grant funds to begin flowing to the winners.

#### Discord

While jokerace does provide the ability for grantees to post their proposals in full, it does not do a very good job of allowing for discussion on proposal. For this it is best to turn to our social media apps. In this case, Discord.

Discord now has a feature for creating forums within a server. Forums differ from other channels in that they allow for longer form posts. It is recommended that grantees post their grant applications in forums, as soon as they can, so people making the decisions of where to place their votes, have a good understanding of what their votes are going to be used for.


# Team-10-MIST-4610-Group-Project-1
# Team Name
Group 10 | 21482
# Team Members
1. [Aniketh Venkateswaran](https://github.com/anivenk033)
2. [Fauz Syed](https://github.com/Fauz-Syed?tab=repositories)
3. [Sean Payne](https://github.com/SeanPayne19)
4. [Phillip Doan](https://github.com/phillipdoan10)

# Problem Description
After meeting with the client, our team has recognized inefficiencies and potential errors in the club operations due to the fact that the soccer organization that our client is in charge of does not have a centralized system where all its data can be stored. To address these issues we have been tasked with creating and operating a database system that connects the different datasets such as clubs, teams, players, staff, tournaments, etc., and will be completely tailored to the wants and needs of the client. In addition, during this project we will create a data model which visualizes the relationships of the entities, we will occupy the datasets with synthetic data, and we will generate queries that provide practical insights into the operations of the organization. Overall the goal of the database is to streamline the club operations, maintain effective and efficient data/datasets, and enhance the experience of the entirety of the organization.

# Data Model
This data model represents a soccer club. It efficiently manages player-team relationships, coaching assignments, payment transactions, sponsorships, facility usage, tournament participation, and player development. This streamlined framework enhances efficiency and performance within the soccer organization.\
The Clubs entity contains information about the clubs such as their unique identifier clubID, the name of the club, the City that the club is located in, and the club's website name. One club comprises many teams, indicated by the identifying relationship between Clubs (Parent Table) and Teams (Child Table), with clubID representing the foreign key derived from the Clubs Entity. One Club can also have many facilities as indicated by the one-to-many identifying relationship between Clubs (Parent Table) and Facility (Child Table), with club_clubID serving as the foreign key derived from the club entity. However, we noticed a slight user error during the data import process. When creating the data model, we accidentally created an extra foreign key attribute as club_facility_ID. This foreign key can be ignored as it is irrelevant to our queries, and our overall data model.\
The Teams entity contains information about the Teams such as their unique identifier teamID, the name of the team, and the age group of the team. One team has many players, hence the identifying one-to-many relationship between Teams (Parent Table) and Players (Child Table), Teams_teamID would serve as a foreign key referencing to the teams table, and Teams_clubID would be a foreign key referencing back to the Clubs table. This gives us the ability to link players to both their team and their club.\
The Players table contains a plethora of information about the players, such as their unique identifier, playerID, the player name, age, gender, position, number, skill level, the team ID for which team they play for, and the Club ID identifying which club their team is a part of. There is an identifying one-to-many recursive relationship inside of the player's table identifying captains with the foreign key captainID, one captain can mentor many players. Many Players can have many Coaches, hence the many-to-many relationship between Players and Coaches. The Player Assignment table serves as the Associative Entity which serves as a bridge between Players and Coaches many to many relationships, including details such as which player is coached by which coach, and the salary for all the coaches. In the coaches' table, there is a one-to-one recursive relationship within the table. This recursive relationship identifies one intern coach for certain coaches. One coach can only have a maximum of one intern coach.\
The Payments Entity contains information about payments such as paymentID which serves as a unique identifier for each payment, the amount of the payment, the date of the payment, and the payment description. This entity has a many-to-many relationship with players and coaches making the player assignment entity the centralized associative entity Players, Coaches, and Payments. Relating the Payments relationship to the other entities is easy because multiple players can have multiple payments such as salary and multiple coaches can have multiple payments. The foreign key for Payments is labeled salaryID in the Player Assignment table. Coaches have an internCoach number of -1 or 0, then you match the interncoach # (not 0 or -1) to the corresponding coachID to find the intern coaches information. The data import process led to a few duplicates, so the coaches with interns are duplicated throughout the Coaches Table. The duplicate contains an internCoach # (not 0 or -1), then you track that internCoach # to the corresponding coachID to find the information on that intern coach!\
The Sponsor's entity contains information about the sponsors, such as a unique identifier for each sponsor utilizing the sponsorID, the sponsor name, contact info, and the sponsorship level. Many facilities can have the same sponsor which is identified by the identifying one to many relationship between the Sponsors Entity (Parent Entity) and the Facility Entity (Child Entity), the foreign key in the Facilities table is facility_sponsor_ID represents the sponsor ID for each facility.\
The Facility entity describes the facilities used for the teams and clubs. They are uniquely identified by their facilityID, along with the name of the facility, the location, and the type of facility. One facility can hold many Training Sessions, hence the one-to-many relationship between Facility (Parent Entity) and Training Sessions (Child Entity), the foreign key facilityID in the Training Sessions Table identifies which facility is used for the specific Training Session. One Facility can also hold many Tournaments hence the identifying one to many relationship between Facilities (Parent Entity) and Tournaments (Child Entity). The foreign key in the Tournaments entity is facilityID to identify which facility is used for which tournament.\
The Tournaments entity describes the tournaments played by the teams and clubs. They are uniquely identified by their tournamentID, along with the name of the tournament, the date, time, and prize money. One tournament can have many matches, however, this is represented by a non-identifying one-to-many relationship between Tournaments (Parent Entity) and Matches (Child Entity). It is non-identifying because friendly matches don’t require a tournament and can be played separately from a tournament.\
The Training Sessions entity describes the Training Sessions using the unique identifier, sessionID, date, location, and session type. One Training Session can have many Drills, hence the identifying one-to-many relationship between Training Sessions (Parent Entity) and Drills (Child Entity). Training Sessions use many pieces of equipment, hence the many-to-many relationship between the Training Sessions entity and the Equipment entity. The associative entity, Drills, helps facilitate the association between Training Sessions and Equipment through Drills. Each row in the Drills table represents a specific drill conducted during a training session and it specifies the equipment used in that drill. This allows for the effective organization of drills within the context of the training sessions.\
![image](https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/22a50923-fcc3-4e2f-9160-9561be32830e)
# Data Dictionary
<img width="449" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/56d54638-b466-4a34-97e4-2594b120cec5">\
<img width="447" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/8da69e05-0bbf-4410-b418-ef5a20cb4b13">\
<img width="449" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/1911f82b-5bde-49bc-8153-002441960039">\
<img width="446" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/81e56358-f8f2-42e2-95a0-6b018977c151">\
<img width="446" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/faf8486a-7af9-439d-82f2-2a9e75326e5b">\
<img width="446" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/e4bd0daa-88f4-4d20-aaa3-cc8b882dee09">\
<img width="446" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/6e86dea0-bfc5-422c-82d4-534e725540ed">
# Queries
<img width="307" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/552d7b0a-0892-40ea-9e3e-e9fb6fc1fde6">\
**Query 1**: List the name of tournaments that take place during Winter and the prize money is more than $5000\
<img width="353" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/6abe714e-cfa6-4148-a364-c6cba4e762f0">\
**Justification**: Hosting tournaments in the winter with prize money exceeding $5000 is important for several reasons. Firstly, it attracts top talent and increases competitiveness among participating teams, leading to higher-quality matches. Additionally, it promotes the sport during a season when there may be fewer competitive events, stimulating interest among fans and potential new participants. Economically, such tournaments can benefit the host city or region by boosting tourism and local businesses. Moreover, they enhance the organization's reputation within the soccer community and attract sponsors seeking exposure to a large audience.\
**Query 2**: Select player gender, count of players, and player position from the Players table, and group the results by both player gender and position\
<img width="215" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/a1eacf0e-c75b-4eb2-a67d-b73e0565d0c9">\
**Justification**: Knowing the number of people and their genders who play each position in a soccer organization is crucial for strategic planning, player development, gender equity, team balance, recruitment, competition management, and player satisfaction. It allows the organization to optimize team performance, promote inclusivity, and create positive experiences for all players involved.\
Query 3: Which coaches make over 200k, and how many players do they oversee\
<img width="347" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/7d3c9725-bb9b-4541-b44a-89f5113a97f5">\
Justification: Knowing which coaches make over $200,000 and the amount of players they oversee is essential for salary management, performance evaluation, resource allocation, player development, team dynamics, recruitment and retention, and promoting equity and fairness within the organization. It enables administrators to make informed decisions and ensure the effective management of coaching staff and player resources.\
Query 4: Which players in each club are older than the average age of players within their respective clubs\
<img width="359" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/190d26f9-368d-47cd-b05a-c0e223974d5d">\
Justification: Older players often bring leadership qualities and experience to the team. Identifying these players allows coaches to leverage their leadership skills to mentor younger players, provide guidance during matches, and contribute to team cohesion. They are often role models for the younger players in the clubs.\
Query 5: What is the average age of the players in each club\
<img width="248" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/9f1e0c5b-7262-42ca-94ec-4b4d2382938f">\
Justification: Knowing the average age of each player in each club within a soccer organization is crucial for team composition, player development, talent identification, succession planning, team cohesion, strategic decisions, and player welfare. It allows clubs to effectively manage their rosters and create environments conducive to the growth and success of their players.\

Query 6: Find the players that do not have a team\
<img width="344" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/1ac3f138-e329-4251-a265-e117b2b185ee">\
Justification: It aids in player recruitment efforts, enabling the organization to target individuals for team membership and expand its player base. Additionally, it facilitates the development of skill enhancement programs tailored to unassigned players, fostering talent growth and preparing them for team participation. Identifying unassigned players also helps in forming new teams or adjusting existing ones, ensuring balanced and competitive rosters. By maximizing available resources and promoting inclusivity, soccer organizations can engage with the community more effectively and foster long-term growth and sustainability.\
Query 7: How many players are there in each age group (U12, U14, U16, U18) for each club\
<img width="346" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/0156b93e-10c5-40f9-8437-14e3bd53fb1f">\
Justification: Knowing the number of people in each group within a soccer organization is crucial for efficient resource allocation, effective team management, and tailored training and development programs. It helps to ensure adequate supervision, maintain safe player-to-coach ratios, and plan budgets accordingly. Additionally, understanding group dynamics contributes to player satisfaction and retention, as players are more likely to stay engaged when they receive personalized attention and support. Overall, having this information enables the organization to optimize operations, enhance player experiences, and achieve its goals more effectively.\
Query 8: List the name of the player and the total amount of payments they have received\
<img width="342" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/22d3c242-5259-466e-9480-18f36d62546a">\
Justification: Knowing the players and the amount of payments they have received is essential for financial transparency, contract management, salary management, tax compliance, player welfare, performance incentives, contract negotiations, and player retention efforts within a soccer organization. It enables clubs to effectively manage their financial resources and ensure that players are compensated fairly and accurately.
Query 9: List the Intern Coaches for each Head Coach, but include the information only if the Head Coach has an assigned intern\
<img width="573" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/fd823658-d171-4280-9818-e77da9de9c1f">\
Justification: Identifying coaches who mentor interns allows the organization to facilitate mentorship and professional development opportunities. Intern coaches benefit from hands-on experience and guidance from experienced coaches, which helps them develop their coaching skills and knowledge.\
Query 10: List how many wins and losses are in each tournament\
<img width="344" alt="image" src="https://github.com/Fauz-Syed/Team-10-MIST-4610-Group-Project-1/assets/166072354/cc9065cd-ad77-4fc7-9af4-5fb72167cd34">\
Justification: Knowing how many wins and losses are in each tournament is essential for performance evaluation, tournament standings, strategic planning, player development, motivation and morale, fan engagement, scouting and recruitment, and organizational evaluation. It enables teams and organizations to make informed decisions and adjustments to improve their performance and achieve success in future tournaments.








# BuendíaLabsInJaamSim
A discrete events model for Buendía Labs emergency vaccination center in Macondo, Colombia.

<img width="806" alt="JaamSim2022-06_tCc8RPzjET" src="https://user-images.githubusercontent.com/63328827/227752743-2a79cc51-8b31-4b7e-8b57-ef07644ae480.png">

This model has been developed along my advisory work with my client Buendía labs in Macondo, Colombia.
(Fictitious names are used for the sake of client’s protection)

Buendía labs took the challenge to vaccinate for KOVID-91 a very big share for the whole population of Macondo. Hence, managers wanted to do the best job possible with their resources. In this regard, they decided to set a list of criteria to maintain the quality of service:
-	Not forcing personnel to work beyond the closing time.
-	Not forcing people to wait that long at lines.
-	Taking the most from the team of physicians, nurses and assistants
-	Vaccinate 70% of Macondo’s population (200,000 inhabitants) as fast as possible.
Their process was inspired in the paper [“Montgomery County's Public Health Service Uses Operations Research to Plan Emergency”]( https://www.jstor.org/stable/20141446), that was about a successful experience in the USA for emergency vaccination. Description of the center, its stages and process are explained in the “Planning Mass-Dispensing and Vaccination Clinic” section of the document. Nevertheless, human and physic resources Buendía labs had were way more restricted than those of Montgomery County’s Public Health Service. 
-	No bus to take patients to the center.
-	Less medical and nursing personnel.
-	Less room to gather people for watching the educational videos.
-	No possibilities of working 24/7 but in the following work schedule:
o	Mondays through Fridays: 7:00 to 12:00 and 14:00 to 17:00
o	Saturdays: 7:00 to 12:00 

  Also, the statistical reports in Macondo regarding KOVID-91 epidemics point out:
-	30% of probability of symptoms.
-	40% of cases could complicate due to previous conditions.
-	50% of probability of exposure considering lockdowns were not necessary in Macondo (and hopefully either not in the rest of the world).
-	78% Macondo’s population has manifested willingness to receive the vaccine.

Given the conditions in which Buendía Labs’ must work, efficiency is the clue to reach challenging goals such as these ones. Managers understand that hiring new personnel must be necessary, but they don’t want to make such a decision without any previous thorough analysis. Thus, building the a JaamSim model has been my main advice for them. With this model they have been able to simulate every scenario, being the first one:
-	Patients can arrive to the center in groups of up to eight people. (Uniformly distributed between one and eight)
-	An interarrival time: Exponentially distributed with mean of 15 minutes.	 

Stage |	Service Time |	Original capacity |	Kind of Staff
| :---: | :---: | :---: | :---: |
Triage (Triaje) |	3 min |	2	| Nurse
Registration (Registro) |	Uniform(0.5 min, 2 min)|	2 |	Assistant
Holding (Espera) |	10 min |	2	| Nurse
Symptoms (Síntomas) |	10 min |	1 |	Nurse
Education (Concienciación) |	15 min |	1* | Assistant
Screening (Chequeo) |	Uniform(5 min, 10 min) |	5 |	Physician
Consultation (Consulta) |	Uniform(5 min, 15 min) |	1	| Physician|
Vaccination (Vacunación) |	Uniform(0.5 min, 2 min) |	4 |	Nurse


*: One room to display the educational videos. There is one assistant to manage entry and exit of people and to operate the screen. The capacity of the room is 10 patients.

To properly simulate the challenge, we bore in mind:
-	Buendía labs strongly demand to accomplish work schedule. Thus, it was observed that every patient leaves the center on time so personnel can leave immediately.
-	At the education stage, process entities must be considered as a “groups” of people for more accurate modeling.
-	A week of work would be the simulation time.
-	Visual indicators for stages’ capacities, human resources utilization, total cycle and queue time, and total of patients vaccinated or not vaccinated are needed.
-	Visual queue length counters next to each stage in red.
-	User can enter capacities for each stage with an input value text object, in blue.
-	Resources may be entered next to their bar indicators.
-	The possibility of sharing human resources among stages has been considered. 
-	The golden question: How many vaccination centers must Buendía labs deploy in Macondo to vaccinate 70% of the population the fastest as possible with the least personnel within the work schedule?
 
A proven valid scenario found so far has been:
| Stage |	Proven valid resources quantities |
| :---: | :---: | 
| Assistants	| 1 |
| Nurses | 5 |
| Physicians | 6 |

Where:
-	The mean cycle time has been 1h 05 min. 
-	The mean waiting time at queues is 27 minutes.
-	472 people went through the process, in which 334 of them were vaccinated. The difference is explained by people who decided not to get the vaccine after the screening in which they would be told if they could present health complications.
-	Patients leave quite on time according to the work schedule. Only a 20 minutes lag was once observed. A condition to accomplish this has been to close the entry of new patients at 10:30 to be ready for lunch time and at 16:00 to be ready at the end of the work day.

To vaccinate 140,000 people in one year, 48 full working weeks have been considered (Easter, Christmas, New Years Eve, and, of course, carnival… This is the Caribbean Colombian coast!). On these conditions they must deploy 9 centers like this one in all Macondo. Nevertheless, if they decide to change work schedule or increasing personnel, this model will help Buendía labs to propose different scenarios to make better decisions. 
The next step to increase this project potential could be:
-	Automatize multiple scenarios runs.
-	Analyze data logs of all scenarios and multiple replications aided by a data visualization dashboard. 

The [model](https://github.com/ArnaldoMatute/Buend-aLabsInJaamSim/blob/main/Buendia%20Labs.cfg) in this repository is just available in Spanish. 
Use  JaamSim release 2022-06 or newer.




# New Document

[question]: What question do we ask? What is the problem as we see it? Our Abstract is too generic.
[goal]: What is the final goal? It is not the money, should be something humanitarian!
[solution]: How we intend to solve the problem? Write down what you think in few sentences.
[model]: I think we will use one of the Linear Programming methods, so we need a cost function that we will optimize. Or at least an idea of it.
[data]: Data insights - the more the better.

Abstract

An international airport is the most populated and busiest travel area where many people used to move around the world. Gate assignment is one of the most important tasks for airport ground operations, which assigns appropriate airport gates with high efficiency reasonable arrangement. 
It is important to notice that flights delays and cancellation have a negative impact on airport performance and do not provide an excellent experience to travelers.
This study aims to propose a new airport gate assignment method to effectively improve the comprehensive operation capacity and efficiency of John F. Kennedy International airport (JFK airport). It will also help to optimize the number of gate allocated to each airline and improve travelers experience.

Methodology approach

As a first level of analysis, the study will give an overview of JFK airport performance and will highlight the delay trend, the number cancellation and the effect of airline performance on airport gate utilization.
As a second level, a linear multiple regression model will be developed to evaluate and predict the impact of airlines delays, cancellation, number of flights, number of passenger and the price/cost of each gate on the number of gate that is allocated to each airline.

Dependant variables:

-	Number of gate allocated per airline

Independent variables:
-	Unique carrier
-	Number of flights per unique carrier
-	Number of delays on arrival
-	Number of delays on departure
-	Cancellation (yes/no)
-	Number of cancellation
-	Cancellation reason
-	Nb of passenger per flight per unique carrier
-	Gate cost
-	Selling gate price
-	Airport revenue
-	Day of the week
-	month


Data understanding

Information from 22 years has been retrieved from airlines transportation database. These datasets are from 1987 to 2008 and are relative to United State airlines performance.

Variable descriptions

| Name              | Description                                                               |
|-------------------|---------------------------------------------------------------------------|
| Year              | 1987-2008                                                                 |
| Month             | 1 - 12                                                                    |
| DayofMonth        | 1 - 31                                                                    |
| DayOfWeek         | 1 (Monday) - 7 (Sunday)                                                   |
| DepTime           | actual departure time (local, hhmm)                                       |
| CRSDepTime        | scheduled departure time (local, hhmm)                                    |
| ArrTime           | actual arrival time (local, hhmm)                                         |
| CRSArrTime        | scheduled arrival time (local, hhmm)                                      |
| UniqueCarrier     | unique carrier code                                                       |
| FlightNum         | flight number                                                             |
| TailNum           | plane tail number                                                         |
| ActualElapsedTime | in minutes                                                                |
| CRSElapsedTime    | in minutes                                                                |
| AirTime           | in minutes                                                                |
| ArrDelay          | arrival delay, in minutes                                                 |
| DepDelay          | departure delay, in minutes                                               |
| Origin            | origin IATA airport code                                                  |
| Dest              | destination IATA airport code                                             |
| Distance          | in miles                                                                  |
| TaxiIn            | taxi in time, in minutes                                                  |
| TaxiOut           | taxi out time in minutes                                                  |
| Cancelled         | was the flight cancelled?                                                 |
| CancellationCode  | reason for cancellation (A = carrier, B = weather, C = NAS, D = security) |
| Diverted          | 1 = yes, 0 = no                                                           |
| CarrierDelay      | in minutes                                                                |
| WeatherDelay      | in minutes                                                                |
| NASDelay          | in minutes                                                                |
| SecurityDelay     | in minutes                                                                |
| LateAircraftDelay | in minutes                                                                |


Data Analysis

For the year 2008, JFK airport has 118.804 flights from 11 different carriers. The top 4 most important carriers are JetBlue Airways with 45% of total traffic followed by Comair Inc. (16%), Delta Air Lines (14%) and American Airlines Inc. (10%).

	Number of flights per carrier at New York John F. Kennedy Airport (JFK)

| Month  | JetBlue Airways (B6) | Delta Air Lines Inc. (DL) | Comair Inc. (OH) | American Airlines Inc. (AA) | Continental Air Lines Inc. (CO) | American Eagle Airlines Inc. (MQ) | United Air Lines Inc. (UA) | Northwest Airlines Inc. (NW) | US Airways Inc. (US) | Mesa Airlines Inc. (YV) | Atlantic Southeast Airlines (EV) |
|--------|----------------------|---------------------------|------------------|-----------------------------|---------------------------------|-----------------------------------|----------------------------|------------------------------|----------------------|-------------------------|----------------------------------|
| Jan-08 | 4,540                | 1,275                     | 1,518            | 1,068                       | 103                             | 667                               | 445                        | 154                          | 172                  | 81                      |                                  |
| Feb-08 | 4,375                | 1,238                     | 1,399            | 996                         | 100                             | 625                               | 430                        | 153                          | 164                  | 75                      |                                  |
| Mar-08 | 4,928                | 1,380                     | 1,372            | 1,035                       | 109                             | 645                               | 447                        | 176                          | 186                  | 78                      |                                  |
| Apr-08 | 4,690                | 1,341                     | 1,230            | 1,019                       | 108                             | 617                               | 464                        | 175                          | 180                  | 77                      |                                  |
| May-08 | 4,425                | 1,422                     | 1,117            | 1,043                       | 107                             | 639                               | 463                        | 182                          | 186                  | 79                      |                                  |
| Jun-08 | 4,444                | 1,434                     | 1,476            | 981                         | 107                             | 616                               | 475                        | 175                          | 180                  | 5                       | 46                               |
| Jul-08 | 4,764                | 1,494                     | 2,508            | 1,048                       | 111                             | 666                               | 472                        | 178                          | 186                  |                         | 76                               |
| Aug-08 | 4,811                | 1,451                     | 2,495            | 1,051                       | 108                             | 640                               | 448                        | 170                          | 175                  | 4                       | 70                               |
| Sep-08 | 3,886                | 1,338                     | 1,446            | 936                         | 29                              | 616                               | 383                        | 150                          | 147                  | 33                      | 2                                |
| Oct-08 | 3,936                | 1,366                     | 1,437            | 961                         |                                 | 605                               | 395                        | 155                          | 147                  | 35                      |                                  |
| Nov-08 | 3,935                | 1,306                     | 1,450            | 872                         |                                 | 687                               | 374                        | 142                          | 171                  | 85                      |                                  |
| Dec-08 | 4,162                | 1,348                     | 1,478            | 936                         |                                 | 713                               | 387                        | 121                          | 182                  | 89                      |                                  |
| Total  | 52,896               | 16,393                    | 18,926           | 11,946                      | 882                             | 7,736                             | 5,183                      | 1,931                        | 2,076                | 641                     | 194                              |








Delay trend IN/OUT in minute for top 4 carriers at New York John F. Kennedy Airport (JFK)
											
| JetBlue Airways (B6) |          |           | Delta Air Lines Inc. (DL) |          |           | Comair Inc. (OH) |          |           | American Airlines Inc. (AA) |          |           |
|----------------------|----------|-----------|---------------------------|----------|-----------|------------------|----------|-----------|-----------------------------|----------|-----------|
|                      | Delay IN | Delay OUT |                           | Delay IN | Delay OUT |                  | Delay IN | Delay OUT |                             | Delay IN | Delay OUT |
| Jan-08               | 12,802   | 35,088    |                           | -812     | 10,728    |                  | -2,735   | 13,609    |                             | 12,309   | 12,988    |
| Feb-08               | 59,040   | 58,630    |                           | 8,423    | 15,828    |                  | 3,349    | 12,305    |                             | 23,575   | 19,025    |
| Mar-08               | 55,435   | 62,378    |                           | 19,313   | 16,728    |                  | 12,785   | 17,595    |                             | 23,961   | 18,935    |
| Apr-08               | 25,965   | 46,178    |                           | 14,109   | 16,439    |                  | 8,420    | 11,200    |                             | 29,958   | 20,459    |
| May-08               | 16,423   | 15,769    |                           | 8,900    | 15,646    |                  | 7,991    | 8,921     |                             | 28,281   | 17,136    |
| Jun-08               | 96,536   | 57,520    |                           | 38,140   | 25,995    |                  | 37,474   | 24,188    |                             | 46,982   | 27,941    |
| Jul-08               | 115,981  | 96,075    |                           | 36,735   | 34,149    |                  | 54,707   | 43,608    |                             | 40,748   | 28,219    |
| Aug-08               | 115,300  | 109,549   |                           | 25,443   | 32,199    |                  | 38,685   | 32,947    |                             | 30,069   | 25,511    |
| Sep-08               | 3,036    | 22,868    |                           | -5,759   | 8,860     |                  | 9,554    | 13,552    |                             | 10,212   | 12,054    |
| Oct-08               | -25,549  | 6,489     |                           | -16,740  | 6,713     |                  | -6,449   | 7,212     |                             | 6,643    | 10,506    |
| Nov-08               | -13,828  | 26,594    |                           | -9,440   | 7,225     |                  | 8,910    | 16,807    |                             | -1,093   | 10,040    |
| Dec-08               | 66,061   | 87,718    |                           | 14,946   | 18,815    |                  | 48,135   | 41,612    |                             | 21,495   | 19,683    |
| Total                | 527,202  | 624,856   |                           | 133,258  | 209,325   |                  | 220,826  | 243,556   |                             | 273,140  | 222,497   |



Cancellation trend 

Cancellation per carrier at New York John F. Kennedy Airport (JFK): Top 4 carriers

| Month  | American Airlines Inc. (AA) | JetBlue Airways (B6) | Delta Air Lines Inc. (DL) | Comair Inc. (OH) | Total cancellation |
|--------|-----------------------------|----------------------|---------------------------|------------------|--------------------|
| Jan-08 | 30                          | 55                   | 16                        | 63               | 164                |
| Feb-08 | 42                          | 113                  | 27                        | 130              | 312                |
| Mar-08 | 24                          | 72                   | 22                        | 83               | 201                |
| Apr-08 | 36                          | 42                   | 6                         | 36               | 120                |
| May-08 | 19                          | 10                   | 7                         | 22               | 58                 |
| Jun-08 | 21                          | 141                  | 14                        | 84               | 260                |
| Jul-08 | 41                          | 188                  | 29                        | 193              | 451                |
| Aug-08 | 20                          | 197                  | 25                        | 203              | 445                |
| Sep-08 | 15                          | 63                   | 19                        | 49               | 146                |
| Oct-08 | 7                           | 18                   | 8                         | 15               | 48                 |
| Nov-08 | 2                           | 37                   | 6                         | 33               | 78                 |
| Dec-08 | 18                          | 127                  | 30                        | 121              | 296                |
| Total  | 275                         | 1,063                | 209                       | 1,032            | 2,579              |



From the cancellation trend, it clearly mentioned that Comair Inc. and JetBlue Airways have the most important number of flights cancellation which represent respectively 5% and 2% of their entire flights.

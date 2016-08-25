# SQL Zoo Joins

####First Question:
```sql
SELECT matchid, player FROM goal 
  WHERE teamid = 'GER'
```

####Second Question:
```sql
SELECT id,stadium,team1,team2
  FROM game WHERE id = 1012
```

####Third Question:
```sql
SELECT player, teamid, mdate
  FROM game JOIN goal ON (id=matchid)
WHERE teamid = 'GER'
```

####Fourth Question:
```sql
SELECT team1, team2, player
  FROM game JOIN goal ON (id=matchid)
WHERE player LIKE 'Mario %'
```

####Fifth Question:
```sql
SELECT player, teamid, coach, gtime
  FROM goal JOIN eteam ON id=teamid
 WHERE gtime<=10
```

####Sixth Question:
```sql
SELECT mdate, teamname 
  FROM game JOIN eteam ON (team1=eteam.id)
WHERE team1 =
  (SELECT eteam.id FROM eteam
WHERE coach = 'Fernando Santos')
```

####Seventh Question:
```sql
SELECT player FROM goal
  JOIN game ON (matchid = id)
WHERE stadium = 'National Stadium, Warsaw';
```
=======================
=====BONUS SECTION=====
=======================

####Eighth Question:
```sql
SELECT distinct player
  FROM game JOIN goal ON matchid = id 
    WHERE (team1='GER' OR team2='GER')
    AND teamid != 'GER'
```

####Ninth Question
```sql
SELECT teamname, COUNT(gtime) as TotalGoals
  FROM eteam JOIN goal ON id=teamid
 GROUP BY teamname
ORDER BY TotalGoals DESC
```

####Tenth Question
```sql
SELECT stadium, COUNT(gtime) as goals
FROM game JOIN goal ON (matchid=id)
GROUP BY stadium
ORDER BY goals DESC
```

####Eleventh Question
```sql
SELECT matchid,mdate, COUNT(*) as goals
  FROM game JOIN goal ON matchid = id 
 WHERE (team1 = 'POL' OR team2 = 'POL')
GROUP by matchid
```

####Twelfth Question
```sql
SELECT matchid, mdate, COUNT(*) as goals
FROM game JOIN goal ON (matchid=id)
WHERE (teamid = 'GER')
GROUP BY matchid
```

####Thirteenth Question
```sql
SELECT mdate, team1,
  SUM(CASE WHEN teamid=team1 THEN 1 ELSE 0 END) score1,
  team2,
  SUM(CASE WHEN teamid=team2 THEN 1 ELSE 0 END) score2
  FROM game JOIN goal ON matchid = id
GROUP BY id
ORDER BY mdate, matchid, team1, team2
```

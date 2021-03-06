Query no.1

``` Sql
SELECT
  day,
  amountJoined,
  amountRetained,
  ROUND(amountRetained/amountJoined, 3) AS fractinalRetention
FROM (
  SELECT
    day,
    COUNT(PL.player_id) AS amountJoined,
    playerRetained AS amountRetained,
  FROM (
    SELECT
      joined AS day,
      COUNT(player_id) AS playerRetained,
    FROM (
      SELECT
        DISTINCT PL.player_id,
        PL.joined,
        MAX(MI.day) - PL.joined AS daysPlayed,
      FROM
        `psyched-circuit-329514.GameCompanyData.player_info` AS PL
      JOIN
        `psyched-circuit-329514.GameCompanyData.matches_info` AS MI
      ON
        PL.player_id = MI.player_id
      GROUP BY
        PL.player_id,
        joined)
    WHERE
      daysPlayed > 30
    GROUP BY
      joined )
  JOIN
    `psyched-circuit-329514.GameCompanyData.player_info` AS PL
  ON
    day = PL.joined
  GROUP BY
    day,
    playerRetained )
ORDER BY
  day
```

Query no.2
```sql
SELECT
  DISTINCT retention,
  AVG(moneySpent) AS averageSpent
FROM (
  SELECT
    CASE
      WHEN (MAX(MI.day) - PL.joined) > 30 THEN 1
    ELSE
    0
  END
    AS retention,
    PL.player_id,
    PL.age,
    PL.location,
    COUNT(PU.item_id) AS itemsBought,
    ROUND(SUM(IT.price), 2) AS moneySpent
  FROM
    `psyched-circuit-329514.GameCompanyData.player_info` AS PL
  JOIN
    `psyched-circuit-329514.GameCompanyData.matches_info` AS MI
  ON
    PL.player_id = MI.player_id
  JOIN
    `psyched-circuit-329514.GameCompanyData.purchase_info` AS PU
  ON
    MI.player_id = PU.player_id
  JOIN
    `psyched-circuit-329514.GameCompanyData.item_info` AS IT
  ON
    PU.item_id = IT.item_id
  GROUP BY
    PL.player_id,
    PL.joined,
    PL.age,
    PL.location)
GROUP BY
  retention
```

Query no.3

```sql
SELECT
  DISTINCT location,
  COUNT(player_id) AS players,
  SUM(moneySpent) AS Spending
FROM (
  SELECT
    CASE
      WHEN (MAX(MI.day) - PL.joined) > 30 THEN 1
    ELSE
    0
  END
    AS retention,
    PL.player_id,
    PL.age,
    PL.location,
    COUNT(PU.item_id) AS itemsBought,
    ROUND(SUM(IT.price), 2) AS moneySpent
  FROM
    `psyched-circuit-329514.GameCompanyData.player_info` AS PL
  JOIN
    `psyched-circuit-329514.GameCompanyData.matches_info` AS MI
  ON
    PL.player_id = MI.player_id
  JOIN
    `psyched-circuit-329514.GameCompanyData.purchase_info` AS PU
  ON
    MI.player_id = PU.player_id
  JOIN
    `psyched-circuit-329514.GameCompanyData.item_info` AS IT
  ON
    PU.item_id = IT.item_id
  GROUP BY
    PL.player_id,
    PL.joined,
    PL.age,
    PL.location)
WHERE
  retention=1
GROUP BY
  location
```
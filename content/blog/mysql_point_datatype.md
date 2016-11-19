---
author: "Damien Roche"
date: 2012-06-20
linktitle: Introduction to MySQL point datatype
title: Short Intro to MySQL point datatype
highlight: true
url: /blog/database/mysql_point_datatype.html
---
The MySQL point data type is extremely useful for storing spatial data like latitude and longitudes.
```
/**
 * Simple table to store a point
 */
CREATE TABLE IF NOT EXISTS device_locations (
    location_id INT(6) AUTO_INCREMENT PRIMARY KEY,
    location POINT NOT NULL,
    last_seen DATETIME NOT NULL
) ENGINE=INNODB;
Inserting data into the table is quite simple by casting your X,Y coordinates to the POINT data type
```

```
INSERT INTO device_locations
    (location, last_seen)
VALUES
    (POINT(-5,10), NOW());
```

Getting your data back out is very easy too by using the X, Y Property Functions a subset of the functions provided in MySQL.

```
SELECT
    location_id,
    X(location) AS x_pos,
    Y(location) AS y_pos,
    last_seen
FROM
    device_locations
ORDER BY last_seen DESC;

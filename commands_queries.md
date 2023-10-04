CREATE TABLE cats (
  id INTEGER PRIMARY KEY,
  name TEXT,
  age INTEGER,
  breed TEXT
);

CREATE TABLE owners (
  id INTEGER PRIMARY KEY,
  name TEXT
);

INSERT INTO owners (name) VALUES ("mugumogu");
INSERT INTO owners (name) VALUES ("Sophie");
INSERT INTO owners (name) VALUES ("Penny");
INSERT INTO cats (name, age, breed) VALUES ("Maru", 3, "Scottish Fold");
INSERT INTO cats (name, age, breed) VALUES ("Hana", 1, "Tabby");
INSERT INTO cats (name, age, breed) VALUES ("Nona", 4, "Tortoiseshell");
INSERT INTO cats (name, age, breed) VALUES ("Lil' Bub", 2, "perma-kitten");

CREATE TABLE cat_owners (
  cat_id INTEGER,
  owner_id INTEGER
);

INSERT INTO cat_owners (cat_id, owner_id) VALUES (3, 2);
INSERT INTO cat_owners (cat_id, owner_id) VALUES (3, 3);
INSERT INTO cat_owners (cat_id, owner_id) VALUES (1, 2);

SELECT cat_owners.owner_id
FROM cat_owners
WHERE cat_id = 3;

SELECT cat_owners.cat_id
FROM cat_owners
WHERE owner_id = 2;

SELECT owners.name
FROM owners
INNER JOIN cat_owners
ON owners.id = cat_owners.owner_id WHERE cat_owners.cat_id = 3;

SELECT cats.name
FROM cats
INNER JOIN cat_owners
ON cats.id = cat_owners.cat_id
WHERE cat_owners.owner_id = 2;

SELECT
  cats.name AS cat_name,
  owners.name AS owner_name
FROM cats
INNER JOIN cat_owners
  ON cats.id = cat_owners.cat_id
INNER JOIN owners
  ON cat_owners.owner_id = owners.id;
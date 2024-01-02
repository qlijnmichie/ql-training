# MySQL Practice - Beginners

## Setup
Download the world database from MySQL by clicking on this link: https://downloads.mysql.com/docs/world-db.zip

Unzip the installed folder the wherever is convenient for you. You can then setup the database locally by following [MySQL’s world database installation guide](https://dev.mysql.com/doc/world-setup/en/world-setup-installation.html).

- [ ] Download and run the `world.sql` file

The `world.sql` database has three tables, shown below for reference:

1. **city**
```sql
CREATE TABLE `city` (
  `ID` int NOT NULL AUTO_INCREMENT,
  `Name` char(35) NOT NULL DEFAULT '',
  `CountryCode` char(3) NOT NULL DEFAULT '',
  `District` char(20) NOT NULL DEFAULT '',
  `Population` int NOT NULL DEFAULT '0',
  PRIMARY KEY (`ID`),
  KEY `CountryCode` (`CountryCode`),
  CONSTRAINT `city_ibfk_1` FOREIGN KEY (`CountryCode`) REFERENCES `country` (`Code`)
)
```

2. **country**
```sql
CREATE TABLE `country` (
  `Code` char(3) NOT NULL DEFAULT '',
  `Name` char(52) NOT NULL DEFAULT '',
  `Continent` enum('Asia','Europe','North America','Africa','Oceania','Antarctica','South America') NOT NULL DEFAULT 'Asia',
  `Region` char(26) NOT NULL DEFAULT '',
  `SurfaceArea` decimal(10,2) NOT NULL DEFAULT '0.00',
  `IndepYear` smallint DEFAULT NULL,
  `Population` int NOT NULL DEFAULT '0',
  `LifeExpectancy` decimal(3,1) DEFAULT NULL,
  `GNP` decimal(10,2) DEFAULT NULL,
  `GNPOld` decimal(10,2) DEFAULT NULL,
  `LocalName` char(45) NOT NULL DEFAULT '',
  `GovernmentForm` char(45) NOT NULL DEFAULT '',
  `HeadOfState` char(60) DEFAULT NULL,
  `Capital` int DEFAULT NULL,
  `Code2` char(2) NOT NULL DEFAULT '',
  PRIMARY KEY (`Code`)
)
```

3. **countrylanguage**
```sql
CREATE TABLE `countrylanguage` (
  `CountryCode` char(3) NOT NULL DEFAULT '',
  `Language` char(30) NOT NULL DEFAULT '',
  `IsOfficial` enum('T','F') NOT NULL DEFAULT 'F',
  `Percentage` decimal(4,1) NOT NULL DEFAULT '0.0',
  PRIMARY KEY (`CountryCode`,`Language`),
  KEY `CountryCode` (`CountryCode`),
  CONSTRAINT `countryLanguage_ibfk_1` FOREIGN KEY (`CountryCode`) REFERENCES `country` (`Code`)
)
```


## Practice

### Processing and Finding
- [ ] What country has the largest population?
- [ ] Create a table with 2 columns (country and language spoken) named as Country and Has_Language, ordered alphabetically by language spoken.
- [ ] In how many countries is Spanish spoken?
- [ ] Which country does the city Nijmegen reside in?
- [ ] How many cities exist in the country Tunisia?
- [ ] Create a table with 2 columns (country | population), where all the counties listed are located in the continent of Asia, and the table is ordered by the population.
- [ ] Which city that starts with ‘J’ has the smallest population?
- [ ] Which country has the highest life expectancy? Which has the lowest? What is the average life expectancy overall?
- [ ] What is the capital city of the country Palestine?

### Creating New Data
- [ ] Add your own fake city to the city table (with a country code that references the second of your fake country codes below)
- [ ] Add two of your own fake countries to the country table
    - [ ] For the first, fill it with as little data as possible
    - [ ] For the second, provide all the data
- [ ] Try making up a continent and using that value when creating a new, fake country to the country table (should get an error)

### Deleting Values and Tables
- [ ] Choose and drop any language you wish from the countrylanguage table
- [ ] Drop all values from the city table
- [ ] Completely delete the country table
- [ ] Verify (if you haven’t already) that the above drops/deletes worked as you expect
- [ ] Drop the whole world database

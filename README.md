Database Project for Library
The scope of this project is to use all the SQL knowledge gained throught the Software Testing course and apply them in practice.

Application under test: Library

Tools used: MySQL Workbench



Database Schema

You can find below the database schema that was generated through Reverse Engineer and which contains all the tables and the relationships between them.
The tables are connected in the following way:

**Table Book ** is connected with **Table ReadingSheet** through a **one to one** relationship which was implemented through **Reader.bookCode** as a primary key and **ReadingSheet.bookCode** as a foreign key
**Table PublishingHouse** is connected with **Table Book** through a **one to one** relationship which was implemented through ** PublishingHouse. PublisherCode** as a primary key and **Book.PublisherCode** as a foreign key
**Table Readerr** is connected with **Tabela ReadingSheet** through a **one to one** relationship which was implemented through **Reader.CNP** as a primary key and **ReadingSheet.CNP** as a foreign key

Database Queries

DDL (Data Definition Language)
The following instructions were written in the scope of CREATING the structure of the database (CREATE INSTRUCTIONS)

    Create database Library;
  
      create table Book(
      bookCode varchar (20) primary key not null,
      BookName varchar (50) not null,
      Author varchar (30) not null,
      NumberOfBooks numeric(5) not null,
      Price numeric (5) not null,
      PublisherCode varchar(25) not null,
      Year numeric (4)not null
      );
  
      create table PublishingHouse (
      PublisherCode varchar(25) primary key not null,
      PublisherName varchar(13) not null,
      Adress varchar(40) not null,
      Telephone varchar(10) not null

      );

      create table Reader (
      CNP numeric(13) NOT null,
      FirstName varchar (20) not null,
      LastName varchar(40) not null,
      City varchar (35) not null,
      Email varchar(30),
      Adress varchar (45),
      Telephone varchar(10)

      );

      create table ReadingSheet(
      FileCode varchar (20) primary key not null,
      bookCode varchar (20),
      CNP numeric(13) NOT null,
      LoanDate date 
      );


After the database and the tables have been created, a few ALTER instructions were written in order to update the structure of the database, as described below:

Inserati aici toate instructiunile de ALTER pe care le-ati scris. Incercati sa includeti instructiuni cat mai variate cum ar fi: - schimbare nume tabela - adaugare sau stergere coloana - redenumire coloana - adaugare proprietati coloana (ex: adaugare auto-increment) - modificare proprietati coloana (ex: modificare tip de data, modificare pozitie coloana etc) - adaugare cheie primara sau secundara (daca nu a fost deja adaugata la crearea tabelei)

DML (Data Manipulation Language)
In order to be able to use the database I populated the tables with various data necessary in order to perform queries and manipulate the data. In the testing process, this necessary data is identified in the Test Design phase and created in the Test Implementation phase.

Below you can find all the insert instructions that were created in the scope of this project:

Inserati aici toate instructiunile de INSERT pe care le-ati scris. Incercati sa folositi atat insert pe toate coloanele (fara sa precizati pe ce coloane se face insert) cat si insert pe cateva coloane (care necesita mentionarea explicita a coloanelor pe care se face insert). De asemenea, incercati sa acoperiti situatia in care inserati mai multe randuri in acelasi timp

After the insert, in order to prepare the data to be better suited for the testing process, I updated some data in the following way:

Inserati aici toate instructiunile de UPDATE pe care le-ati scris folosind filtrarile necesare astfel incat sa actualizati doar datele de care aveti nevoie

DQL (Data Query Language)
After the testing process, I deleted the data that was no longer relevant in order to preserve the database clean:

Inserati aici toate instructiunile de DELETE pe care le-ati scris folosind filtrarile necesare astfel incat sa stergeti doar datele de care aveti nevoie

In order to simulate various scenarios that might happen in real life I created the following queries that would cover multiple potential real-life situations:

Inserati aici toate instructiunile de SELECT pe care le-ati scris folosind filtrarile necesare astfel incat sa extrageti doar datele de care aveti nevoie Incercati sa acoperiti urmatoarele:
- where
- AND
- OR
- NOT
- like
- inner join
- left join
- OPTIONAL: right join
- OPTIONAL: cross join
- functii agregate
- group by
- having
- OPTIONAL DAR RECOMANDAT: Subqueries - nu au fost in scopul cursului. Puteti sa consultati tutorialul asta si daca nu intelegeti ceva contactati fie trainerul, fie coordonatorul de grupa

Conclusions
Inserati aici o concluzie cu privire la ceea ce ati lucrat, gen lucrurile pe care le-ati invatat, lessons learned, un rezumat asupra a ceea ce ati facut si orice alta informatie care vi se pare relevanta pentru o concluzie finala asupra 

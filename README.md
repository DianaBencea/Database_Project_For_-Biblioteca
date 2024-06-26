# Database Project for Library

The scope of this project is to use all the SQL knowledge gained throught the Software Testing course and apply them in practice.

Application under test: Library

Tools used: MySQL Workbench




## Database Schema


You can find below the database schema that was generated through Reverse Engineer and which contains all the tables and the relationships between them.
The tables are connected in the following way:


<img width="361" alt="image" src="https://github.com/DianaBencea/Database_Project_For_-Library/assets/151565785/cacfa02f-689f-4936-b3e9-ae4508a236a9">


**Table Book ** is connected with **Table ReadingSheet** through a **one to one** relationship which was implemented through **Reader.bookCode** as a primary key and **ReadingSheet.bookCode** as a foreign key
**Table PublishingHouse** is connected with **Table Book** through a **one to one** relationship which was implemented through ** PublishingHouse. PublisherCode** as a primary key and **Book.PublisherCode** as a foreign key
**Table Readerr** is connected with **Tabela ReadingSheet** through a **one to one** relationship which was implemented through **Reader.CNP** as a primary key and **ReadingSheet.CNP** as a foreign key

## Database Queries

## DDL (Data Definition Language)

The following instructions were written in the scope of CREATING the structure of the database (CREATE INSTRUCTIONS)

    Create database Library;
  
      create table Book(
      bookCode varchar (20) primary key not null,
      BookName varchar (50) not null,
      Author varchar (30) not null,
      NumberOfBooks numeric(5) not null,
      Price numeric (5) not null,
      PublisherCode varchar(25) not null,
      Year numeric (4)not null);
  
      create table PublishingHouse (
      PublisherCode varchar(25) primary key not null,
      PublisherName varchar(13) not null,
      Adress varchar(40) not null,
      Telephone varchar(10) not null);

      create table Reader (
      CNP numeric(13) NOT null,
      FirstName varchar (20) not null,
      LastName varchar(40) not null,
      City varchar (35) not null,
      Email varchar(30),
      Adress varchar (45),
      Telephone varchar(10));

      create table ReadingSheet(
      FileCode varchar (20) primary key not null,
      bookCode varchar (20),
      CNP numeric(13) NOT null,
      LoanDate date);


After the database and the tables have been created, a few ALTER instructions were written in order to update the structure of the database, as described below:

    alter table reader add fax varchar(12);
    alter table reader modify fax char(10);
    alter table reader drop column fax;

## DML (Data Manipulation Language)

In order to be able to use the database I populated the tables with various data necessary in order to perform queries and manipulate the data. In the testing process, this necessary data is identified in the Test Design phase and created in the Test Implementation phase.
Below you can find all the insert instructions that were created in the scope of this project:

    -- insert data into Book table
    insert into book values ('1', 'Poezii', 'Mihai Eminescu', '6', '30', '1', '1923');
    insert into book values ('2', 'Ion', 'Liviu rebreanu', '4', '67', '2', '1948');
    insert into book values ('3', 'Baltagul', 'Mihail sadoveanu', '5', '80', '4', '1992');
    insert into book values ('4', 'Morometii', 'Marin Preda', '7', '56', '6', '1970');
    insert into book values ('5', 'O noapte furtunoasa', 'Ioan Luca Caragiale', '6', '100', '3', '1999');
    insert into book values ('6', 'Cuvinte Potrivite', 'Tudor Arghezi', '8', '63', '1', '1917');

     -- insert data into PublishingHouse table
    insert into PublishingHouse (PublisherCode, PublisherName, Adress, Telephone)
    values('1', 'Corint', 'Bld Magheru nr 1', '0722745892');
    insert into PublishingHouse (PublisherCode, PublisherName, Adress, Telephone)
    values('2', 'Humanitas', 'Bld Iuliu Maniu nr 40', '0765453453');
    insert into PublishingHouse (PublisherCode, PublisherName, Adress, Telephone)
    values('3', 'Teora', 'Bld Marasesti nr 2A', '0745370812');
    insert into PublishingHouse (PublisherCode, PublisherName, Adress, Telephone)
    values('4', 'Litera', 'Bld Aviatorilor nr 16', '0744354323');
    insert into PublishingHouse (PublisherCode, PublisherName, Adress, Telephone)
    values('5', 'Libris', 'Bld Unirii nr 2', '0754532900');
    insert into PublishingHouse (PublisherCode, PublisherName, Adress, Telephone)
    values('6', 'Rao', 'Sos Pipera nr 8', '0754532900');

    -- insert data into Reader table
    insert into reader values
    ('1900505465343','Vasilescu','Sergiu','Bucuresti', 'svasilescu@yahoo.com' ,'bld Ion Mihalache nr 5', '0723242567');
    insert into reader values
    ('1900808465343','Popescu','Mihai','Bucuresti', 'mpop@yahoo.com' ,'bld Iuliu Maniu nr 4', '0766786577');
    insert into reader values
    ('2770204465223','Vasile','Stefania','Brasov', 'stefi@yahoo.com' ,'bld Calea Bucuresti nr 70', '0721350908');
    insert into reader values
    ('2760204465112','Marin','Ioana','Brasov', 'yoyo@yahoo.com' ,'Sos Miahai Bravu nr 2', '0722228978'),
    ('2880204465221','Manole','Madalina','Iasi', 'madatza@yahoo.com' ,'Str Primaverii nr 12', '0744765843'),
    ('1880204465223','Marcu','Raducu','Iasi', 'mraducu@yahoo.com' ,'Str Lalelelor nr 44', '0787564323');


    -- insert data into ReadingSheet table
    insert into ReadingSheet( FileCode, bookCode, CNP, LoanDate)
    values('1', '3','1880204465223', '1988-02-04');
    insert into ReadingSheet( FileCode, bookCode, CNP, LoanDate)
    values('2', '2','2880204465221', '1988-02-04');
    insert into ReadingSheet( FileCode, bookCode, CNP, LoanDate)
    values('3', '1','2760204465112', '1976-02-04');
    insert into ReadingSheet( FileCode, bookCode, CNP, LoanDate)
    values('4', '4','2770204465223', '1977-02-04');
    insert into ReadingSheet( FileCode, bookCode, CNP, LoanDate)
    values('5', '6','1900808465343', '1990-08-08');
    insert into ReadingSheet( FileCode, bookCode, CNP, LoanDate)
    values('6', '5','1900505465343', '1990-05-05');

After the insert, in order to prepare the data to be better suited for the testing process, I updated some data in the following way:
  
    update reader set city = 'Constanta' where FirstName = 'Popescu';
    update reader set lastName = 'Elena' where CNP like'%112';
    update book set price = '99' where PublisherCode = '5';


## DQL (Data Query Language)

After the testing process, I deleted the data that was no longer relevant in order to preserve the database clean:

    delete from Reader where CNP='2880204465223';

In order to simulate various scenarios that might happen in real life I created the following queries that would cover multiple potential real-life situations:


afiseaza toate inregistrarile din tabela  reader, unde CNP-ul se termina cu cifrele 223 si orasul este Iasi

    select * from reader
    where CNP like '%223' and city = 'Iasi';
   
afiseaza toate inregistrarile din tabela  reader, unde CNP-ul se termina cu cifrele 223 ori orasul este Iasi

    select * from reader
    where CNP like '%223' or city = 'Iasi';

afiseaza Numele cititorilor din tabela  reader, unde CNP-ul se termina cu cifrele 223 ori cei care sunt din orasul Iasi

    select FirstName from reader
    where CNP like '%223' or city = 'Iasi';

afiseaza Numele si Prenumele cititorilor  din tabela  reader, care locuiesc in orasul Iasi

    Select firstName, LastName  from Reader
    where city = "Iasi";

afiseaza Numele cartii si autorul din tabela book pntru toate cartile care au pretul mai mare de 50 lei si anul aparitiei inainte de 1990

    select bookName, Author from book
    where price> 50 and Year <1990;

afiseaza cate carti gsesti in tabela book aparute inainte de 1990

    select count(bookName) from book 
    where year <1990;

afiseaza toate inregistrarile din tabelele book  si ReadingSheet sub forma unui singur tabel

    select * from reader
    left join ReadingSheet
    on reader.CNP= ReadingSheet.CNP;

afiseaza toate inregistrarile din tabelele book  si PublisingHouse sub forma unui singur tabel

    select * from book
    inner join PublishingHouse
    on book.PublisherCode= PublishingHouse.PublisherCode;


afiseaza numele cartii, Autorul  si totalul preturilor din tabela book, unde codul editurii este 3

    select BookName, Author, sum(price) from book 
    where PublisherCode>'3'
    group by BookName, Author;


    



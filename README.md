# Manufacturing

/* 
Manufacturing data Analysis */

create database pro;
use pro;
select *  from manu;
 
 /* Manufacturing Qty /*
 select concat(round(sum(Manufactured_Qty)/1000000),'M') from Manu;

/* Processed Qty /*
select concat(round(sum(Processed_Qty)/1000000),'M') from Manu;

/* Rejected Qty/*
select concat(round(sum(Rejected_Qty)/1000),'K') from Manu; 

/* Wastage Qty /*
select sum(Rejected_Qty) as Wastage_Qty from Manu;

/* Wastage % /*
select concat(round(sum(Rejected_Qty)/sum(Processed_Qty)*100), '%') from manu;

/* Total Employees /*
select count(distinct Empcode) from manu;

/* Total Buyers /*
select count(distinct Buyer) from manu;

/* Department Wise Manufactured And Rejected Qty /*
select DepartmentName, concat(round(sum(Manufactured_Qty)/10000),'K') as Manufactured_Qty ,concat(round( sum(rejected_Qty)/1000),'K') as Rejected_Qty from manu group by DepartmentName;
 
/* Emp Wise Rejected Qty /*
select EmpName,sum(Rejected_Qty) As Rejected_Qty from manu group by EmpName order by Rejected_Qty desc limit 10;

/* Machine wise Rejected Qty /*
select MachineCode ,sum(Rejected_Qty) As Rejected_Qty from manu group by MachineCode order by Rejected_Qty desc limit 8;

/* production trend /*
 select monthname(FiscalDate) as MonthName, sum(manufactured_Qty) as Manufactured_Qty from manu group by MonthName order by MonthName desc;


 /* Top 8 Buyers wise  Manufactured Qty /*
select Buyer ,Concat(round(sum(Manufactured_Qty)/1000000),'M') as Manufactured_Qty  from manu group by Buyer;
 
 
 /* Per Day cost By operation /*
select OperationName, concat(round(sum(pdmc)/1000),'K') from manu group by OperationName ;
 
 /*  Machine/Employee Wise Rejected Qty /*
 Select Machine_or_Emp, sum( Rejected_Qty) as Rejected_Qty from manu group by Machine_or_Emp order by Rejected_Qty desc limit 20;


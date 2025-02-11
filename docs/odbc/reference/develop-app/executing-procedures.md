---
title: "Executing Procedures"
description: "Executing Procedures"
author: David-Engel
ms.author: v-davidengel
ms.date: "01/19/2017"
ms.service: sql
ms.subservice: connectivity
ms.topic: reference
helpviewer_keywords:
  - "SQL statements [ODBC], procedures"
  - "procedures [ODBC], executing"
---
# Executing Procedures
ODBC defines a standard escape sequence for executing procedures. For the syntax of this sequence and a code example that uses it, see [Procedure Calls](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 To execute a procedure, an application performs the following actions:  
  
1.  Sets the values of any parameters. For more information, see [Statement Parameters](../../../odbc/reference/develop-app/statement-parameters.md), later in this section.  
  
2.  Calls **SQLExecDirect** and passes it a string containing the SQL statement that executes the procedure. This statement can use the escape sequence defined by ODBC or DBMS-specific syntax; statements that use DBMS-specific syntax are not interoperable.  
  
3.  When **SQLExecDirect** is called, the driver:  
  
    -   Retrieves the current parameter values and converts them as necessary. For more information, see [Statement Parameters](../../../odbc/reference/develop-app/statement-parameters.md), later in this section.  
  
    -   Calls the procedure in the data source and sends it the converted parameter values. How the driver calls the procedure is driver-specific. For example, it might modify the SQL statement to use the data source's SQL grammar and submit this statement for execution, or it might call the procedure directly using a Remote Procedure Call (RPC) mechanism that is defined in the data stream protocol of the DBMS.  
  
    -   Returns the values of any input/output or output parameters or the procedure return value, assuming the procedure succeeds. These values might not be available until after all other results (row counts and result sets) generated by the procedure have been processed. If the procedure fails, the driver returns any errors.

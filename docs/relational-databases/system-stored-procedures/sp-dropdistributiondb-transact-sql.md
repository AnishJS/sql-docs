---
title: "sp_dropdistributiondb (Transact-SQL) | Microsoft Docs"
description: Drops a distribution database and files used by it if they are not used by another database. This stored procedure runs at the Distributor on any database.
ms.custom: ""
ms.date: "03/03/2017"
ms.service: sql
ms.reviewer: ""
ms.subservice: replication
ms.topic: "reference"
dev_langs: 
  - "TSQL"
f1_keywords: 
  - "sp_dropdistributiondb_TSQL"
  - "sp_dropdistributiondb"
helpviewer_keywords: 
  - "sp_dropdistributiondb"
ms.assetid: b6dd1846-2259-4d29-93af-a70a5d25a0c5
author: markingmyname
ms.author: maghan
---
# sp_dropdistributiondb (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Drops a distribution database. Drops the physical files used by the database if they are not used by another database. This stored procedure is executed at the Distributor on any database.  
  
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```  
  
sp_dropdistributiondb [ @database= ] 'database'  
```  
  
## Arguments  
`[ @database = ] 'database'`
 Is the database to drop. *database* is **sysname**, with no default.  
  
## Return Code Values  
 **0** (success) or **1** (failure)  
  
## Remarks  
 **sp_dropdistributiondb** is used in all types of replication.  
  
 This stored procedure must be executed before dropping the Distributor by executing **sp_dropdistributor**.  
  
 **sp_dropdistributiondb** also removes a Queue Reader Agent job for the distribution database, if one exists.  
  
 To disable distribution, the distribution database must be online. If a database snapshot exists for the distribution database, it must be dropped before disabling distribution. A database snapshot is a read-only offline copy of a database, and is not related to a replication snapshot. For more information, see [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## Example  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistributiondb-tr_1.sql)]  
  
## Permissions  
 Only members of the **sysadmin** fixed server role can execute **sp_dropdistributiondb**.  
  
## See Also  
 [Disable Publishing and Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Replication Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  

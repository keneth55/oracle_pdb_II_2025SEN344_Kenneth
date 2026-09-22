# Assignment II: Oracle Pluggable Database Management Report

**Date:** September 22, 2026  
**Course:** Advanced Database Systems / PL-SQL  
**Environment:** Oracle Database 21c Express Edition (XE) installed directly on Windows 11

> **Pluggable Database (PDB):** A portable, self-contained logical database that functions as a regular standalone database to applications while operating within a shared Container Database (CDB).

---

## 1. Overview of Tasks

This assignment demonstrates the administrative lifecycle of a Pluggable Database (PDB) within an Oracle Container Database (CDB) environment.

The exercise covers the following database administration tasks:

- Installing Oracle Database 21c Express Edition (XE) on Windows 11.
- Creating a Pluggable Database.
- Opening the newly created PDB.
- Saving the PDB state for persistence after database restarts.
- Verifying the PDB operational status.
- Closing the PDB.
- Deleting the PDB and its associated datafiles.
- Documenting the challenges encountered during the implementation.

---

## 2. Oracle Environment Configuration

The practical exercise was performed using the following environment:

| Configuration | Details |
|---|---|
| **Operating System** | Windows 11 |
| **Database** | Oracle Database 21c Express Edition (XE) |
| **Installation Method** | Direct installation on Windows 11 |
| **Database Client** | Oracle SQL Developer Extension for Visual Studio Code |
| **Administrative Access** | `SYSDBA` |

Oracle Database 21c Express Edition (XE) was downloaded and installed directly on the Windows 11 operating system. The Windows installation package was extracted and installed using the Oracle Database XE installer.

Database administration and SQL execution were performed using the Oracle SQL Developer Extension for Visual Studio Code with `SYSDBA` privileges.

---

## 3. Oracle Database Installation

Oracle Database 21c Express Edition (XE) for Microsoft Windows 64-bit was downloaded from the official Oracle Database XE download page.

The installation process involved:

1. Downloading the Windows version of Oracle Database 21c Express Edition.
2. Extracting the downloaded installation package.
3. Running the `setup.exe` installer.
4. Completing the Oracle Database XE installation wizard.
5. Configuring the database using the installation settings.
6. Accessing the installed Oracle Database through the SQL development environment.

Oracle's official installation documentation provides the Windows installation procedure, including extracting the downloaded ZIP package and running `setup.exe`. :contentReference[oaicite:1]{index=1}

---

## 4. Core Task Execution

### Task A: Pluggable Database Creation

The target Pluggable Database was created within the Oracle Container Database using the following SQL command:

```sql
CREATE PLUGGABLE DATABASE ken_db_20252SEN241
ADMIN USER keneth_plsqlauca_20252SEN241
IDENTIFIED BY "3LO15"
FILE_NAME_CONVERT=('pdbseed','ken_db_20252SEN241');
```

After creating the PDB, it was opened using:

```sql
ALTER PLUGGABLE DATABASE ken_db_20252SEN241 OPEN;
```

To ensure that the PDB would retain its open state after a database restart, the state was saved using:

```sql
ALTER PLUGGABLE DATABASE ken_db_20252SEN241 SAVE STATE;
```

**Result:** The Pluggable Database was successfully created and opened.

---

### Task B: Environment Status Verification

The operational status of the newly created PDB was verified using the Oracle dynamic performance view `V$PDBS`.

The following SQL query was executed:

```sql
SELECT name, open_mode
FROM v$pdbs
WHERE name = 'ken_DB_20252SEN241';
```

The query was used to confirm that the PDB was operating in `READ WRITE` mode.

**Verification Result:**

```text
ken_DB_20252SEN241    READ WRITE
```

**Verification Status:** `READ WRITE`

This verification confirmed that the PDB was successfully created and was available for normal read and write operations.

---

### Task C: Pluggable Database Deletion

After completing the required PDB operations, the database was closed before being removed from the Oracle environment.

First, the PDB was closed using:

```sql
ALTER PLUGGABLE DATABASE _kendb_20252SEN241 CLOSE IMMEDIATE;
```

The PDB was then permanently removed together with its associated datafiles:

```sql
DROP PLUGGABLE DATABASE ken_db_20252SEN241 INCLUDING DATAFILES;
```

**Result:** The PDB was successfully closed and deleted from the Oracle database environment.

---

## 5. Challenges Faced and Solutions

### Challenge 1: Oracle Database Installation

One of the challenges encountered during the assignment was installing and configuring Oracle Database 21c Express Edition on Windows 11.

**Solution:**  
The official Windows version of Oracle Database 21c Express Edition was downloaded and installed directly on the Windows 11 operating system using the provided Oracle installer.

---

### Challenge 2: Database Connection and Administration

Another challenge was establishing an administrative connection to the Oracle Database and executing the required PDB commands.

**Solution:**  
The Oracle SQL Developer Extension for Visual Studio Code was used to connect to the Oracle Database. Administrative operations were performed using the `SYSDBA` role.

---

### Challenge 3: PDB Lifecycle Management

Managing the lifecycle of the Pluggable Database required correctly executing commands for creation, opening, state persistence, closing, and deletion.

**Solution:**  
The required Oracle SQL commands were executed sequentially. The `V$PDBS` view was also used to verify the PDB status before proceeding with the deletion process.

---

### Challenge 4: Oracle Enterprise Manager (OEM)

Oracle Enterprise Manager (OEM) was not accessed during this practical exercise.

Therefore, no OEM-based activity or verification is claimed as part of the implementation.

---

## 6. Integrity Statement

I hereby declare on my honor that the database configurations, SQL commands, query outputs, and technical administration activities documented in this submission represent the work performed individually in my Oracle Database environment.

---

## 7. Required Submission Details

| Item | Details |
|---|---|
| **Repository Link** | (https://github.com/keneth55/oracle_pdb_II_2025SEN344_Kenneth) |
| **Operating System** | Windows 11 |
| **Database** | Oracle Database 21c Express Edition (XE) |
| **Installation Method** | Direct installation on Windows 11 |
| **Database Client** | Oracle SQL Developer Extension for Visual Studio Code |
| **Administrative Role** | `SYSDBA` |
| **PDB Name Created** | `ken_DB_20252SEN241` |
| **PDB Status** | `READ WRITE` |
| **Issues Encountered** | Yes |
| **PDB Deleted** | Yes |

---

## 8. Conclusion

The assignment successfully demonstrated the basic administrative lifecycle of an Oracle Pluggable Database.

Oracle Database 21c Express Edition was installed directly on Windows 11. The PDB `ken_DB_20252SEN241` was then created, opened, configured to preserve its state after database restarts, and verified using the `V$PDBS` view.

After completing the required operations, the PDB was closed and deleted together with its associated datafiles.

The practical exercise provided hands-on experience with Oracle Database 21c XE installation, PDB lifecycle management, SQL-based verification, and database administration on a Windows 11 environment.

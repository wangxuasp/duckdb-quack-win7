# duckdb-quack-win7


The official Quack extension for DuckDB v2.0.0 cannot run on Windows 7. This is because the official build calls CreateFile2 / CreateFileMappingFromApp / MapViewOfFileFromApp — Windows 8+ functions — from KERNEL32.

For these newer APIs, a new library has been written to implement them, while all other functions continue to be called from KERNEL32.

Deployment:

Copy w7k32.dll and quack.duckdb_extension into the same directory as duckdb.exe.


Duckdb v2.0.0 Quack官方扩展不能在Windows 7下运行。 原因官方制会从 KERNEL32 调 CreateFile2 / CreateFileMappingFromApp / MapViewOfFileFromApp的Windows 8+函数。针对这些高版本API，写新库实现，其他函数继续从KERNEL32调。

部署：
复制w7k32.dll、quack.duckdb_extension与duckdb.exe同目录

运行：
```bash
duckdb -unsigned
load './quack.duckdb_extension';
load './httpfs.duckdb_extension';
CALL quack_serve('quack:localhost', token = 'super_secret');
```

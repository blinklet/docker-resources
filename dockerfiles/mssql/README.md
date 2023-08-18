# MS SQL Server with AdventureWorks database

Creates the AdventureWorks LT database on a
container running SQL Server. You need to specify the 
SA user password when you build the image, as shown:

```bash
docker build \
--tag adventureworks-lt2 \
--build-arg passwd=A8f%h45dx23a .
```
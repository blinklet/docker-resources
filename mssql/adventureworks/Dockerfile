# Run the following command (or similar)
# docker build -t adventureworkslt --build-arg passwd=A8f%h45dx23a
FROM mcr.microsoft.com/mssql/server
ARG passwd
ENV ACCEPT_EULA Y
ENV MSSQL_SA_PASSWORD $passwd
RUN mkdir -p /var/opt/mssql/backup \
    && wget -P /var/opt/mssql/backup \
          https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksLT2022.bak \
    && /opt/mssql/bin/sqlservr --accept-eula & sleep 15 \
    && /opt/mssql-tools/bin/sqlcmd \
    -S localhost -U SA -P "$passwd" \
    -Q 'RESTORE DATABASE AdventureWorksLT \
        FROM DISK = "/var/opt/mssql/backup/AdventureWorksLT2022.bak" \
        WITH \
        MOVE "AdventureWorksLT2022_Data" \
        TO "/var/opt/mssql/data/AdventureWorksLT2022.mdf", \
        MOVE "AdventureWorksLT2022_Log" \
        TO "/var/opt/mssql/data/AdventureWorksLT2022_log.ldf"' \
    && pkill sqlservr

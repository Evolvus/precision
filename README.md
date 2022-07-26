Unzip it and you should have 3 folders.
tar -xvf precision100.tar.gz

1. NATIVE
2. finone-3.7-finacle-11.8.1
3. OPERATORS

You need to do the following where u downloaded the zip file

cp -R ./NATIVE enbd-finone-finacle

cd enbd-finnone-finacle;

./configure-project.sh FILE <path to finone-3.7-finacle-11.8.1 folder"> "ENBD Finnone Finacle -KSA"

echo "PRECISION100_CONNECTION,ORACLE,precision100,Welcome123,mig" > ./conf/.connections.env.sh;

./bin/install-connect-operators.sh <path to OPERATORS folder>/connect-operators/ oracle

./bin/install-operators.sh <path to OPERATORS folder>/operators sql-plus;

./bin/install-operators.sh <path to OPERATORS folder>/operators loader;

./bin/install-operators.sh <path to OPERATORS folder>/operators smart-loader;

./bin/install-operators.sh <path to OPERATORS folder>/operators spool;

./bin/install-operators.sh <path to OPERATORS folder>/operators map-file;

./bin/install-operators.sh <path to OPERATORS folder>/operators smart-map-file;

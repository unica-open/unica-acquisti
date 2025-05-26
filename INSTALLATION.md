# INSTALLATION

## Local environment
- For the local development/testing environment, at least one Java EE8-compliant
AS server instance MUST be installed. It is not strictly required to have more
than one instance of the AS server.
- A JMS queue MUST be registered with the JEE context and be available to the
application runtime. The JMS queue MUST be esposed with destination
`queue/CPassQueue` to allow for registration at startup.
- A proxy web server MAY be useful for JS development, by defining a proxy to
the source directories. Depending on the AS server, the proxy may be configured
on it (please refer to the documentation of the server for informations on how
to do so).
- A compliant version of the DBMS MUST be used. The development and runtime are
based on a PostgreSQL 15.4 instance, but any compliant solution should work.
Note that the following extensions MAY, SHOULD or MUST be installed
  - MUST be installed
    - plpgsql
    - pgcrypto
    - uuid-ossp
  - SHOULD be installed (note that the DBA views depend on these extensions.
  Therefore these are to be considered in the MUST section were the DBA views
  desired)
    - adminpack
    - pg_stat_statements
  - MAY be installed
    - pg_buffercache
    - tablefunc
- The datasource MUST be esposed to the JEE context. The project requires the
use of two such datasources, one for the business component `cpassbe` and one
for the reporting component `cpassrepeng`.\
These datasources MUST be exposes to JNDI with the following names:
  - `java:jboss/datasources/cpassbeDS`
  - `java:jboss/datasources/cpassrepengDS`
- A Dockerized environment MAY help with the local development. We do not as of
now provide such environment nor configuration.
- So as to prevent multiple developers to each overwrite one's own properties
for local development, each project that MAY require local configuration has no
such profile file, and the file with the corresponding name is ignored by the
versioning system; its content MUST be reconstructed by example of the singlings
properties files.
- The project components MUST be compiled in the following order (so as to
correctly configure the dependencies):
  - The following MAY be compiled in any order:
    - `cpassrepeng`
    - `cpassscript`
    - `cpassbatch`
  - The following projects SHOULD be compiled in the given order,
  notwithstanding the possibility of a local, separed development environment:
    - `cpassfe` (note that the `/dist` folder MAY be used as a dependency for 
    the `cpassbe/angular` project)
    - `cpassbe`
- Configure the DBMS via the scripts in the `cpassdb` project.
- Configure the User Manual by deploying the compiled ouput of the `cpassdb`
project.
- Install the report templates in the `cpassreptpl` in an accessible folder.
- Install the scripts in `cpassscript` in an accessible folder in a Linux-like environment.
- Install the user manual documents, contained in the `cpassmanual` component, under the /htdocs folder of the apache web server. 
- To test the backend resources, the preferred way is to deploy the backend
project and use a REST client to access the resources.

## Production environment
For the production environment, the same configuration for the local environment
may be used. We strongly suggest against using an exact replica of such
configuration due to the load on the server.

- A load balancer MAY be configured at least for the REST resources.
- The DMBS and AS environments SHOULD be kept separated. The added overhead due
to the TCP connection between two distinct machines is far overshadowed by the
load distribution.
- It is recommended to protect the URLs by preponing a WAF to the DMZ.
- It is recommended to implement a OAuth server to mediate the authentication
experience.
- The `cpassfe` project MUST be compiled before the `cpassbe` project (the
definitions given for MAY/SHOULD in the "Local environment" section are to be
changed to MUST).

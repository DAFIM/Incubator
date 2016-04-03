
Distributed and Federated Identiy Management (DAFIM)
====================================================

Incubator: Place for testing out, proove of concepts etc.

Start date: 2016-03-29

Dear reader,

We are a diverse group of people who would like to find an easy way to install and use a self-hosted and federated single-sign on service that does not depend on a central identity provider like github or google. More specifically: assume that there is a number of independent administrative domains under the same umbrella A, e.g. all cooperative housing projects in a town or all local fair.coop nodes, with their own list of registered users. I - as a user of domain A.X - would like to be able to authenticate myself at another domain A.Y (which has established previously a bilateral trust relationship with domain X) by just clicking on a SSO button, e.g., "Your federated identity A". Authorization should be handled by the application itself, which then may require group relations of users (access and supervisor rights as well as visibility of users to groups). And we would like all this functionality to be hosted on the individual servers of the domains X and Y, as a self-hosted service, and of course to be free software, without dependencies and lock-ins. Do we ask too much? :-)

We are currently looking into: LDAP, 389 directory server, OpenID, shibboleth, kerberos, DACS ID, penrose, WSO2. For documentation, user stories and splitting up tasks we have set up a scrum project on https://tree.taiga.io/project/heribender-distributed-identity-management

Looking forward to your suggestions, and feel free to join!
# ORCID Integration

## Introduction

This page describes ORCID integration with MD-SOAR.

## ORCID Authority

MD-SOAR implements the stock DSpace "ORCID Authority" integration, see
<https://wiki.lyrasis.org/display/DSDOC7x/ORCID+Authority>.

This functionality modifies the "Author(s)" field in the submission form to
provide dynamic lookup of authors in Solr and from the ORCID website.

Author information is indexed in the "authority" core running in Solr.

### crontab.txt Changes

The ORCID Authority functionality requires that the DSpace "index-authority"
script runs daily to update the Solr "authority" index.

### Populating the Solr "authority" core in the Local Development Environment

To populate the Solr "authority" core in the local development environment,
run the following command when the DSpace backend is running:

```bash
$ docker exec dspace /bin/bash -c '/dspace/bin/dspace index-authority'
```

Depending on the contents of the database, the command may take hours to run.
For most purposes, the script can likely be stopped once the Solr "authority"
core has begun to be populated with entries.

## ORCID Credentials

The situation with ORCID credentials is somewhat confused, and there does not
appear to be a simple straightforward answer.

The ORCID API documentation and tutorials would lead you to believe that you
need ORCID credentials to access any part of the ORCID API.

As attested to, however, by

* <https://github.com/DSpace/DSpace/issues/8836>
* <https://groups.google.com/g/orcid-api-users/c/0gXLWIxi9GU>

it is possible to access the ORCID public sandbox:

```text
orcid.domain-url= https://sandbox.orcid.org
orcid.api-url = https://pub.sandbox.orcid.org/v3.0
```

without any credentials. Experimentation with what is believed to be the
"production" public API endpoint:

```text
orcid.domain-url= https://orcid.org
orcid.api-url = https://pub.orcid.org/v3.0
```

also seems to work without credentials.

In the past, SSDR developed an application that integrated more closely with
ORCID (<https://github.com/umd-lib/orcid-umd>), and for which "member" (as
opposed to "public") credentials were obtained. These credentials are in the
"ORCID Production ID" section of the "Developer Resources/Identities.docx"
document in Box. These credentials work with the following endpoint:

```text
orcid.domain-url= https://orcid.org
orcid.api-url = https://api.orcid.org/v3.0
```

While the existing credentials work, they are associated with the decommissioned
"orcid-umd" applicaiton, so we may wish to obtain new credentials for MD-SOAR,
expecially as the credentials are from the University of Maryland, College Park
account, and not USMAI.

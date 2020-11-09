ACWIC Training Provider Integration Microservices
=================================================

There is on of two suites of microservices.
This provides the API endpoints operated by Training Providers,
so they can administer their integration
and so their customers (Aged Care Providers)
can browse their catalogue and procure taining services.

The code for this site is hosted at
https://github.com/ACWIC/training-provider-coordinator

The compliment to this suite is one for Aged Care Providers,
documented at {other document url}.

diagram: this one coloured (other one grey)

The purpose of this repository is to demonstrate
how the suite of microservices can be hosted.
Two methods are supported:

* Using docker-compose.
  Fully self-contained (including backing services).
  Actively used for development and testing,
  also an example of how it might be deployed
  in any container-hosting environment.
* Using Amazon Web Services (AWS).
  Specifically; AWS Lambda (serverless compute platform),
  using an API Gateway and S3 storage service.
  This is an example of hosting the system
  using cost-effective utility infrastructure.

The README file
(at https://github.com/ACWIC/training-provider-coordinator/blob/main/README.md )
contains technical documentation on these deployment scenarios.

The AWS deployment demonstrates how the system can be hosted
with at negligible operating cost.
In this configuration,
annual operating cost for a SME training provider
would be approximately equivalent to one cup of coffee per year.
Large scale training providers
are likely to need sophisticated integration
with existing systems.
In that situation, these microservices could be used as a proxy layer
or equivalent endpoints could be surfaced on existing systems.
The purpose of supporting interoperability through standaisation
is served either way.


Components
----------

The microservice suite is provided by three components.

 * **Admin Service**, used by the Training Provider to maintain
   access, publish their course catalogue and process enrolments.
   Because this is used privately by the Training Provider,
   it does not form part of the 3rd party integration surface
   and could be safely omitted in implementations
   where there more convenient methods exist.
 * **Enrolment Service**, used by Aged Care Providers
   to procure training services.
 * **Course Catalogue**, used by Aged Care Providers
   to discover opportunities to enroll staff in training
   that will meet their needs.


.. uml:: architecture.uml

Each of these components has an open-source reference implementation
that demonstrates the API using a low-cost object-store backing service.


Admin Service
^^^^^^^^^^^^^

Documentation https://acwic-training-provider-admin.readthedocs.org

Source Code: https://github.com/ACWIC/training-provider-admin

Live Endpoints:

 * Development Environment https://wpz8gp45w1.execute-api.us-east-1.amazonaws.com/dev/admin/docs
 * POC Environment https://6l2n6aweqg.execute-api.us-east-1.amazonaws.com/prod/admin/docs


Enrolment Service
^^^^^^^^^^^^^^^^^

Documentation: https://acwic-training-provider-enrolment.readthedocs.org

Source Code: https://github.com/ACWIC/training-provider-enrolment

Live Endpoints:

* Development Environment https://wpz8gp45w1.execute-api.us-east-1.amazonaws.com/dev/enrolment/docs
* POC Environment https://6l2n6aweqg.execute-api.us-east-1.amazonaws.com/prod/enrolment/docs



Course Catalogue
^^^^^^^^^^^^^^^^

Documentation: https://acwic-training-provider-catalogue.readthedocs.org

Source Code: https://github.com/ACWIC/training-provider-catalogue

Live Endpoints:

* Development Environment https://wpz8gp45w1.execute-api.us-east-1.amazonaws.com/dev/catalogue/docs
* POC Environment https://6l2n6aweqg.execute-api.us-east-1.amazonaws.com/prod/catalogue/docs

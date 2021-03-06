---
layout: article
title: Reference Cloud Infrastructure
category: try
---

A StratusLab reference infrastructure is available and offers access
to external third parties in order to test and evaluate our cloud
solution.  This infrastructure is built with the latest stable
releases of the StratusLab distribution and provides two types of
cloud services:

The physical cloud-computing infrastructure is located in two sites

* Athens, Greece - operated by [GRNET][grnet] (cloud.grnet.stratuslab.eu)
* Paris, France - operated by [LAL][lal] (cloud.lal.stratuslab.eu)

The project's [Marketplace][marketplace], containing existing virtual
machine images metadata, is hosted by [Trinity College Dublin (TCD),
Ireland][tcd].

Registration
------------

To register on the StratusLab Reference infrastructure please go to
the [registration page][ref-infra-reg].

For user authentication two different mechanisms are supported

* Username/password pair generated by the StratusLab registration service
* Digital certificate issued by an [IGTF][igtf] accredited Certification
    Authority. In this case authentication can be done directly using this
    certificate or by generating a VOMS proxy certificate signed from the
    above.

During your enrollment you may chose either authentication method. For
the certificate based one, on the registration page you will have to
provide Distinguished Name as it appears in your certificate.

Once your request is approved you will be sent an email with the
details for accessing the cloud service.


What I need to access the StratusLab reference cloud?
-----------------------------------------------------

You will need to [install the StratusLab client tools][client-install]
that allow you to access remotely the cloud and to control the
lifecycle of your Virtual Machine instances. They also allow you to
create entries for the Marketplace, generate your own VM appliances
based on pre-existing images which then can be reference from the
Marketplace and instantiated in the cloud.

The endpoints for invoking the cloud services are 

* cloud.grnet.stratuslab.eu (compute/storage)
* cloud.lal.stratuslab.eu (compute), pdisk.lal.stratuslab.eu (storage)

To configure the above endpoints in the client tools see the [user
client installation instructions][client-install].

Which virtualization technologies do you use?
---------------------------------------------

The StratusLab distribution uses the [OpenNebula][one] toolkit for
virtual machine life-cycle management.  The client-side tools
communicate with the OpenNebula endpoint through the native XML-RPC
protocol provided by the service.

StratusLab, out-of-the-box, is certified for the KVM hypervisor.

What services are offered?
--------------------------

With StratusLab v2 you can instantiate and manage the lifecycle of
virtual machines, including volumes and basic network configuration
(e.g. public, private).

The [Marketplace][marketplace] is publicly accessible and offers base
OS images for various Linux distributions including:

* ttylinux
* CentOS
* Fedora
* Ubuntu

External users also have the ability to upload their own base images
and appliances to the repository. For instructions on how to prepare
your own appliance and upload it on the StratusLab Marketplace consult
the [documentation][documentation].

Users may instantiate VMs with the following predefined hardware
profiles (default: m1.small):

      Type              CPU        RAM       SWAP
      c1.medium       1 CPU     256 MB    1024 MB
      c1.xlarge       4 CPU    2048 MB    2048 MB
      m1.large        2 CPU     512 MB    1024 MB
    * m1.small        1 CPU     128 MB    1024 MB
      m1.xlarge       2 CPU    1024 MB    1024 MB
      t1.micro        1 CPU     128 MB     512 MB

It is also possible to compose custom VM CPU/RAM/SWAP configurations.


On what physical infrastructure are the reference cloud services running?
-------------------------------------------------------------------------

###GRNet

The cloud service is running on 16 dual quad core Intel Xeon E5520
nodes, with HyperThreading enabled. One additional node is used as the
service frontend.  In total, we provide 256 logical cores that can be
used from by VM instances.  Each node is configured with 48 GByte main
memory. The base OS we use is Linux CentOS 6.3.

Storage is provided by a centralized storage server which currently
serves a total of 3 TByte of storage shared among all the nodes with
NFSv3.

###LAL

The cloud at LAL consists of 10 DELL servers each with 24 CPU cores
and 32 GB of RAM.  There is a total of 20 TB of disk space available
via a RAID6 system.

What is the firewall policy?
----------------------------

No firewall restrictions are applied externally to the VMs. All ports
are open for end-user applications at GRNET.  Commonly-used ports are
open at LAL for the virtual machines.

Users are responsible to configure their own port restrictions inside
the VM images and for the overall security of the image in general.

What Quality of Service is provided?
------------------------------------

Currently the StratusLab cloud services are provided as is with no
guarantees about the availability and stability of the service. We are
making the best effort to provide a stable cloud infrastructure but at
the moment we cannot guarantee that a VM instance might not crash or
temporarily be unavailable due to a software or network problem.

How can I deploy my own cloud service?
--------------------------------------

You can use StratusLab distribution v2.x to deploy your own cloud
services.  The software is open source and available from the project
repositories.  Currently we support CentOS 6 Linux distribution and
two modes of installation

* [Manual Installation][manual-install], or
* [Quattor][quattor].

How can I get more information and support?
-------------------------------------------

You should direct any inquiries related to the above services to
support@stratuslab.eu. Please use the same contact for reporting
problems or requesting any special arrangements for the cloud service
setup. Notice that as with the infrastructure itself the support
services are currently provided on best effort basis.

[grnet]: http://www.grnet.gr
[lal]: http://www.lal.in2p3.fr
[marketplace]: https://marketplace.stratuslab.eu
[tcd]: http://www.tcd.ie
[ref-infra-reg]: https://register.stratuslab.eu:8444/
[igtf]: http://www.igtf.net/
[client-install]: /try/2012/01/10/try-user-cli-installation.html
[get-started]: http://stratuslab.eu/doku.php/release:users
[one]: http://www.opennebula.org 
[documentation]: /documentation/
[manual-install]: /install/2012/09/25/install-cloud-services-installation.html
[quattor]: http://quattor.org/

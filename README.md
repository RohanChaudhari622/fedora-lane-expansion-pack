# Fedora Lane Expansion Pack - Secure RHEL Gold Image Project

## Project Overview

This project demonstrates the creation of a customized Red Hat Enterprise Linux (RHEL) Gold Image using RHEL Image Builder and deploying it on Amazon Web Services (AWS).

The objective of this project is to create a standardized, secure, and reusable Linux server image for Fedora Lane's server environment.

## Project Workflow

Fedora Lane Requirements

        |
        v

Create RHEL Image Builder Blueprint
(TOML Configuration File)

        |
        v

Build Customized RHEL Image
(Compose Process)

        |
        v

Generate RAW Disk Image

        |
        v

Upload RAW Image to AWS S3

        |
        v

Import Image using AWS VM Import/Export

        |
        v

Create Amazon Machine Image (AMI)

        |
        v

Launch AWS EC2 Instance

        |
        v

Apply Security Configuration

        |
        v

Verify Services and Security Settings


## Business Problem

Fedora Lane was facing multiple Linux server management challenges:

- Different server configurations across environments
- Difficulty tracking administrative changes
- Longer deployment and recovery time
- Requirement for a standard and secure server platform

To solve these problems, a customized RHEL Gold Image was created using RHEL Image Builder.


## Solution

The RHEL Gold Image provides:

- Standardized server configuration
- Repeatable server deployments
- Security hardening
- Pre-configured software packages
- Consistent operating environment

The image can be reused to launch multiple identical AWS EC2 instances.


## Technologies Used

- Red Hat Enterprise Linux 10.2
- RHEL Image Builder
- AWS EC2
- AWS S3
- AWS VM Import/Export
- AWS IAM
- SELinux
- Firewalld
- Apache HTTP Server
- Git and GitHub


## RHEL Image Builder Implementation

RHEL Image Builder was used to create a customized operating system image.

A blueprint was created in TOML format.

The blueprint defines:

- Required packages
- System customizations
- Users and groups
- Services
- Filesystem configuration
- Security settings


Workflow:

Blueprint

    |

    v

Compose

    |

    v

Customized RHEL Image


## AWS Deployment Implementation

The generated RHEL image was deployed to AWS using the following process:


RHEL Image Builder

        |

        v

RAW Image

        |

        v

Amazon S3 Bucket

        |

        v

AWS VM Import/Export

        |

        v

Amazon Machine Image (AMI)

        |

        v

EC2 Instance


## Security Configuration


### SSH Configuration

SSH was hardened according to security requirements.

Default SSH port:

22


Configured SSH port:

2222


Security changes:

- Disabled root login
- Disabled password authentication
- Enabled SSH key-based authentication


### Apache HTTP Server Configuration

Apache HTTP Server was configured for web service access.

Default Apache port:

80


Configured Apache port:

35443


SELinux was configured to allow Apache traffic on the custom port.

Command used:

semanage port -a -t http_port_t -p tcp 35443


### Firewall Configuration

Only required ports were allowed.

Allowed ports:

2222/tcp - SSH

35443/tcp - HTTP


Firewall verification command:

firewall-cmd --list-ports


Expected output:

2222/tcp 35443/tcp


## Verification


### Check SSH Port

Command:

ss -tlnp | grep sshd


Expected:

*:2222



### Check Apache Port

Command:

ss -tlnp | grep httpd


Expected:

*:35443



### Check SELinux Status

Command:

getenforce


Expected:

Enforcing


## Repository Structure


fedora-lane-expansion-pack/

├── README.md

├── blueprint/

│   └── fedora-lane-blueprint.toml

├── scripts/

├── docs/

└── screenshots/


## Important Notes

The following files should not be uploaded to GitHub:

- AWS private key files (.pem)
- AWS access keys
- RAW disk images
- Password files
- Subscription credentials


## Skills Demonstrated

- Linux System Administration
- Red Hat Enterprise Linux
- RHEL Image Builder
- AWS Cloud Deployment
- AWS EC2 and IAM
- VM Import/Export
- SELinux Configuration
- Firewall Management
- Apache Configuration
- SSH Hardening
- Git Version Control


## Author

Rohan Chaudhari

Fedora Lane Expansion Pack Project

Technologies:

RHEL | AWS | Linux Administration | Cloud Computing

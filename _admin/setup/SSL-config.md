---
title: [Configure SSL]
tags: [Security_SSL]
keywords: tbd
last_updated: tbd
summary: "SSL provides authentication and data security"
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
You should use SSL (secure socket layers) for sending data to and from ThoughtSpot. SSL provides authentication and data security. This section applies to both SSL to enable secure HTTP and secure LDAP.

## About SSL
Many IT departments require SSL for their applications that access data. To use SSL with ThoughtSpot, you'll need your company's own SSL certificate. The certificate is issued per domain, so if you want to use SSL for both HTTP and LDAP, you will need two separate certificates - one for the HTTP domain and one for the LDAP domain.

If you do not have an SSL certificate:

-   Check with your IT department to see if they already have an SSL certificate you can use.
-   If not, you will need to obtain the certificate from an issuing authority.
-   Alternatively, you may disable SSL if you don't want the security it provides by using the command `tscli ssl off`.

There are many SSL vendors to choose from. Check with your existing Web hosting provider first, to see if they can provide the certificate for you.

When you apply for the SSL certificate, you may specify a SAN, wildcard, or single domain certificate. Any of these can work with ThoughtSpot.

## Configure SSL for web traffic

This procedure shows how to add SSL (secure socket layers) to enable secure HTTP (HTTPS) in ThoughtSpot. To set up SSL, you will need:

-   The SSL certificate
-   The private key
- The Certificate Signing Request. You can generate a CSR in several ways. Most often, you generate a CSR and a new private key [at the same time](#csr-new-private-key). If you already have a private key, [use it to generate a CSR](#csr-existing-private-key).

When you generate a Certificate Signing Request, you handle sensitive data. Therefore, ThoughtSpot recommends that its customers generate their own CSRs.

{: id="csr-new-private-key"}
Follow these steps to generate a CSR and a private key. You need a computer you can run Linux commands on, and a recent version of *openssl*.

1. `ssh` into one of your ThoughtSpot nodes.
    ```
    ssh admin@<node_IP>
    ```
2. Run the command to generate a CSR and private key pair:
    ```
    openssl req -new -newkey rsa:2048 -nodes -out csr.pem -keyout pk.key[-subj "/key1=value1/key2=value with space/"]
    ```

    Note the following parameters:
    * ThoughtSpot supports a 2048 or 4096 bit key.
    * `subj`: a common subject. Logically equivalent to the `-dname` property of *keytool*. Alternatively, you can skip this flag, and `openssl` prompts you to enter this information interactively.
    * Optionally, run `add-multivalue-rdn` to allow multiple values to be set for the same key.
    * Run `man req` for more details.

{: id="csr-existing-private-key"}
If you already have a private key, you can use it to generate a CSR. Follow these steps to generate a CSR with an existing private key:

1. `ssh` into one of your ThoughtSpot nodes.
    ```
    ssh admin@<node_IP>
    ```
2. Run the command to generate a CSR and private key pair:
    ```
    openssl req -new -key <private_key_file> -nodes -out csr.pem[-subj "/key1=value1/key2=value with space/"]
    ```

    Specify the existing private key file. Refer to the parameters listed above.

To install the SSL certificate:

1. Follow the instructions from your certifying authority to obtain the certificate. This is usually sent via email or available by download.
2. Copy the certificate and key files to ThoughtSpot:

      ```
      $ scp <key> <certificate> admin@<IP_address>:<path>
      ```

3. Log in to the Linux shell using SSH.
4. Change directories to where you copied the certificate:

    ```
    $ cd <path>
    ```

5. Issue the `tscli` command to install the certificate:

    ```
    $ tscli ssl add-cert <key> <certificate>
    ```

6. To test that the certificate was installed correctly, [Log in to the ThoughtSpot application](logins.html#log-in-to-the-thoughtspot-application).

     You should see that the application's URL begins with `https://`.

## Set the recommended TLS version

There are a couple of security vulnerabilities due to SSL certificates supporting older versions of TLS (Transport Layer Security). This procedure shows you how to set the recommended TLS version to avoid these vulnerabilities.

The PCI (Payment Card Industry) Data Security Standard and the FIPS 140-2 Standard require a minimum of TLS v1.1 and recommends TLS v1.2.

ThoughtSpot supports SSL v3, TLS v1.0, and TLS v1.1 for backwards compatibility. However, the recommended version is TLS v1.2. Therefore, to set the recommended TLS version:

1.  Enable your web browser to support TLS v1.2. This can be done in your browser's advanced settings.
2.  Log in to the Linux shell using SSH..
3.  Issue the following command:

    ```
    tscli ssl set-min-version 1.2
    ```

    This will block all usage of older versions.

## Additional resources
As you develop your expertise in authentication and security, we recommend the following ThoughtSpot U course:
* [Nginx SSL](https://training.thoughtspot.com/authentication-security/610523){:target="_blank"}

See other training resources at <br/>
<a href="https://training.thoughtspot.com/" target="_blank"><img src="{{ "/images/ts-u.png" | prepend: site.baseurl  }}" alt="ThoughtSpot U"></a>    

---

copyright:
  years: 2015, 2021
lastupdated: "2021-07-05"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository, authentication, personal access token, SSH key

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.gitrepos}}
{: #git_working}

Collaborate with your team and manage your source code with a Git repository (repo) and issue tracker that is hosted by IBM and built on [GitLab Community Edition](https://about.gitlab.com/){: external}. For more information about GitLab, see the [GitLab documentation](https://us-south.git.cloud.ibm.com/help){: external}.
{: shortdesc}

Invite only people that you have a personal or business relationship with to collaborate on a project. Users that use an invitation to a Git repo for purposes other than to collaborate on a project might have their access to the service suspended or revoked.
{: important}

Both GitHub and the Git command line are accessible alternatives to GitLab.
{: note}

Don't store regulated data in files or issues within Git repos. The procedures for regulated data are currently not in place.
{: tip}

The [{{site.data.keyword.gitrepos}} tool integration](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-grit) supports teams to manage code and collaborate in many ways:
   * Manage Git repos through fine-grained access controls that keep code secure
   * Review code and enhance collaboration through merge requests
   * Track issues and share ideas through the issue tracker
   * Document projects on the wiki system

Because this tool integration is built on GitLab Community Edition and hosted by IBM on the {{site.data.keyword.cloud_notm}} Platform, a few GitLab options are not available. For example, Delivery Pipeline provides continuous integration and continuous delivery for {{site.data.keyword.Bluemix_notm}}; therefore, the continuous integration features in GitLab are not supported. In addition, the admin functions are not available because they are managed by IBM.
{: tip}

## Using {{site.data.keyword.gitrepos}} with toolchains
{: #git_toolchains}

You can use a template that contains either a {{site.data.keyword.gitrepos}} or GitHub tool integration as a starting point to create a toolchain that you can add Git repositories (repos) to. Alternatively, you can start with an empty toolchain and add either a {{site.data.keyword.gitrepos}} or GitHub tool integration to it. By using a toolchain, you can associate Git repos with your resource groups or Cloud Foundry orgs and your {{site.data.keyword.contdelivery_short}} service instance. 

For more information about using toolchains with Git, see [Creating toolchains with Git](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_git).


## Using {{site.data.keyword.gitrepos}} locally
{: #git_locally}

You can locally access the Git repos that are stored in {{site.data.keyword.gitrepos}}. For instructions to set up Git locally, see [Start using Git on the command line](https://us-south.git.cloud.ibm.com/help/gitlab-basics/start-using-git){: external}.

{{site.data.keyword.gitrepos}} supports HTTPS connections only that use TLS1.2. If you use Eclipse to connect, you might be required to specify this protocol for your Java&trade; version by adding `-Dhttps.protocols=TLSv1.2` to your eclipse.ini file and then restarting Eclipse.
{: tip}

## Authenticating with {{site.data.keyword.gitrepos}}
{: #git_authentication}

Your {{site.data.keyword.cloud_notm}} login and password are only used to authenticate with {{site.data.keyword.gitrepos}} in a web browser. You cannot use your {{site.data.keyword.cloud_notm}} user credentials to authenticate from external Git clients. To complete remote Git operations, such as `clone` or `push`, from your local Git repo, you must use a personal access token or SSH key to authenticate with {{site.data.keyword.gitrepos}}.

The display name that appears for you throughout {{site.data.keyword.gitrepos}} is populated from your {{site.data.keyword.cloud_notm}} login information. This name might be visible to other users when they search for users to add to their projects. You can update the name that is displayed for you throughout {{site.data.keyword.gitrepos}} from your [Profile page](#git_update_name).

### Creating a personal access token
{: #create_pat}

To authenticate with your Git repo over HTTPS, you must create a personal access token.
{: tip}

1. On the {{site.data.keyword.gitrepos}} User Settings dashboard, on the [Access Tokens page](https://us-south.git.cloud.ibm.com/profile/personal_access_tokens){: external}, type the name of the application that you want to create an access token for. For example, `Git CLI`.
1. Optional: Choose an expiry date for the access token.
1. Select the **api** checkbox to create a personal access token that uses api as the scope.
1. Click **Create Personal Access Token**. Make note of your access token in a secure location for future use.
1. On the [Account page](https://us-south.git.cloud.ibm.com/profile/account){: external}, in the Change username section, find your {{site.data.keyword.gitrepos}} username. Your username is also displayed as the first segment of the URL for any personal Git repos that you create.
1. Use your {{site.data.keyword.gitrepos}} username and personal access token to authenticate with your Git repo from an external Git client.

To learn more, see [Personal access tokens](https://us-south.git.cloud.ibm.com/help/api/README.html#personal-access-tokens){: external}.

### Creating an SSH key  
{: create_ssh }

To create an SSH key, see [How to create your SSH Keys](https://us-south.git.cloud.ibm.com/help/gitlab-basics/create-your-ssh-keys){: external}. Accessing your repositories with SSH authentication might require more configuration for proxies and firewalls.

To learn more, see [SSH](https://us-south.git.cloud.ibm.com/help/ssh/README){: external}.

### Verifying host key fingerprints
{: verify_fingerprints }

The first time that you connect to a server by way of Git over SSH, the Git client prompts you to accept the host key fingerprint of the server. You can use the following host key fingerprints to verify SSH connections with the {{site.data.keyword.cloud_notm}} {{site.data.keyword.gitrepos}} servers. Proceed with the connection only if the host key fingerprint matches the specified value for the server that is provided in the following code snippets. 

```
au-syd.git.cloud.ibm.com:
  ECDSA:
    SHA256:oUpjbxJ+UVIlBvcdcKuprZ0JEtCWkTu1yFTdfFHoEF8
    MD5:ca:34:27:f1:49:fd:b4:9d:e8:ce:d2:7b:99:a1:dd:98
  ED25519:
    SHA256:uUqxTjqUQuBjmQGynGb8pXX6FQ2Ag0VLAh4TtuSZMAQ
    MD5:87:ad:c9:26:bd:7f:bc:a8:1c:dc:07:ca:aa:d3:8c:9e
  RSA:
    SHA256:y+QM+SbgQ7SqzQXqwmJTPD0jni+qsDdqZg/sOgOFWbY
    MD5:70:71:95:b5:2a:b4:04:ad:12:b4:77:c6:cf:fe:35:c8
```
{: screen}

```
ca-tor.git.cloud.ibm.com:
  ECDSA:
    SHA256:xqeLs5qKCCNd/SmSTgFktFJW8nTqnF5BmwJSZggguJI
    MD5:fb:41:1a:b4:8c:4d:95:c3:67:d9:eb:4a:b1:94:c2:cb
  ED25519:
    SHA256:mT5EGA/63iaHQZrFkXevP+T/qaFN39JChMGUJtla4nE
    MD5:6f:f2:4e:0e:90:0b:2b:e7:fc:f8:d2:1a:16:35:16:fc
  RSA:
    SHA256:mNvCu12YAUeJVCNfiHNfBKgezh0zgwdwxBs8wXnhPP8
    MD5:60:d6:6a:2f:0c:db:52:e1:20:17:a9:3f:3f:fb:4d:91
```
{: screen}

```
eu-de.git.cloud.ibm.com:
  DSA:
    SHA256:c7Bm79CLA5y4tmnI+jB+wYp8esbIUcOSMxzHtU+hhNY
    MD5:28:b7:ff:67:70:39:16:ed:fb:8a:8b:3c:26:45:b9:56
  ECDSA:
    SHA256:cRQsJFaZLfnQb4xOH68uZvWxuVXe0UQ9Z+ks/9dotnc
    MD5:f3:02:a4:c4:63:d6:3b:30:79:fa:37:7c:ba:2c:9e:81
  ED25519:
    SHA256:ZVuqymHanu+N1P+OJCwHcoRlzjpvGnjV001Mo8BFEzg
    MD5:84:90:72:ec:7d:ff:0e:72:01:b7:08:16:f2:76:21:87
  RSA:
    SHA256:33om5cGnbUduaEeKH+116IMzu2mMCHKOLTNPkmF/lNk
    MD5:b3:8f:02:34:12:03:8c:41:8e:4d:be:56:1c:fe:c8:8c
```
{: screen}

```
eu-gb.git.cloud.ibm.com:
  DSA:
    SHA256:Nt0JS/AQDue0WY7X/xRC5Weu3RTplWABACiCOku8CRc
    MD5:bc:a5:a2:5b:7b:c3:3d:7d:6e:d5:37:eb:08:a1:77:d3
  ECDSA:
    SHA256:UZPNkP+gRMINcgWSN50AeiDsOgnJGGTPXFxI/ASryag
    MD5:f2:29:e2:f0:b2:33:bd:8d:19:7d:f0:41:9a:a5:f0:fe
  ED25519:
    SHA256:k2VN8B5ouxW+mvyp/nX3Dq7U571rluVcMx0z1iUCnU0
    MD5:c6:b1:a7:4b:c7:c2:cf:38:17:32:f5:f7:8d:5b:53:a3
  RSA:
    SHA256:5hSoluX8hoPrChwtWZH0rEzz3Cn5bQP18cZ7xj17Wbg
    MD5:e4:3b:99:ae:4b:ff:f5:f7:96:cf:cf:9a:38:3f:c7:65
```
{: screen}

```
jp-osa.git.cloud.ibm.com:
  ECDSA:
    SHA256:k+FNBh6Yvth9bWyvKnfreYhS+3s/+2MX7q2ci/tFAY0
    MD5:a8:71:f1:dc:7a:28:9c:b6:fc:c6:54:1f:1c:c5:9c:08
  ED25519:
    SHA256:I62KQpR+VBmaJnInUj5AkStPA/Hpu555/tHBQjRjU7Q
    MD5:dc:29:99:b3:4c:2a:e3:e7:b3:9b:b2:00:74:d2:b3:89
  RSA:
    SHA256:FPyK4sO5dzIVI/aL9Ril8GIK+uv2jiNVnTqYKDgkF24
    MD5:18:4f:38:05:c8:68:61:e5:08:dc:a3:61:2d:13:45:c1
```
{: screen}

```
jp-tok.git.cloud.ibm.com:
  DSA:
    SHA256:jX4dD9ojut+OCzEtmsR6hDpK+gJ8g0B5V5k+beFzj7E
    MD5:5c:62:d4:35:32:63:5a:66:79:e3:bb:be:59:ce:41:a5
  ECDSA:
    SHA256:ppgYQJFtPxGlx5tWLKT+aKC535C8g4Xz4Uej2BXrd1k
    MD5:4c:60:e5:cd:0c:b9:3e:8e:25:dd:64:b3:7b:28:de:86
  ED25519:
    SHA256:xWVpw3fnjJB78HjTJOLQijjuCiQRXcPrCQ+5+rgzVLg
    MD5:0a:8f:2f:55:62:9b:c5:51:ab:4b:da:e9:81:e9:02:52
  RSA:
    SHA256:OGttrbZoUWU5/6yjxYq9kO+VCXdQB1JkTc9shgbzrE0
    MD5:c2:83:e8:3b:a8:b6:c5:da:cc:4c:26:b5:38:86:74:13
```
{: screen}

```
us-east.git.cloud.ibm.com:
  DSA:
    SHA256:onqeRZxk/GaxBVY+Bxl97UgW5rBQzTH1dJ7sGJDFUp8
    MD5:d0:82:ab:e7:43:4d:92:68:70:b9:23:44:c0:5a:e3:8a
  ECDSA:
    SHA256:IuHvGWVB3vBJNeZ/4SRKpVgRLZHB2FbmJfU5Toek4Hk
    MD5:ff:22:19:1e:83:0d:f2:bd:5d:32:84:c5:04:65:be:f6
  ED25519:
    SHA256:lxLtQ1Cdn5SG0ZClB9wFLSHODhJofaCUs37LdUnubNU
    MD5:97:10:bd:0e:e2:e4:84:bc:fb:71:36:99:02:02:f7:66
  RSA:
    SHA256:TF8Pcst2F9Ek3p3cJlXz06zMwwZkoq+d23r4URtOPD8
    MD5:f2:77:0c:e3:79:41:33:f5:fa:95:ce:cc:d1:dd:62:d0
```
{: screen}

```
us-south.git.cloud.ibm.com:
  DSA:
    SHA256:EX4AoOpgTqHDmZ97Klhgkz06+rSNDfe+AHZBnXzW+oc
    MD5:bc:67:d0:95:80:1f:1e:c3:70:4a:66:dd:57:3b:53:d7
  ECDSA:
    SHA256:BQx1OpGLx8cTkoL6RmftFgTGFHBz2tKPICJm5My4fa8
    MD5:2e:96:56:70:15:19:21:d6:96:d4:78:6e:84:eb:e9:d7
  ED25519:
    SHA256:XvuvoW6oaJjzb3BnCBrdB03B0Mbfu1Eb1/hmoLdoPDQ
    MD5:e1:02:84:2c:af:d1:e7:b0:0c:6f:9c:0c:ab:c1:ec:fb
  RSA:
    SHA256:PEAncMcnz8jNEOmBabCtJ13cg0oGI0YxLOMWVOkDgjc
    MD5:74:31:4e:57:e7:c7:12:c4:c5:96:78:f4:18:8d:63:60
```
{: screen}

You can use following code snippet to verify the host key fingerprint for a headless connection to Git over SSH, by connecting to the us-south.git.cloud.ibm.com server. To use this code for a different server, update the `HOST` and `EXPECTED FINGERPRINT` values.

```
HOST="us-south.git.cloud.ibm.com"
EXPECTED_FINGERPRINT="SHA256:PEAncMcnz8jNEOmBabCtJ13cg0oGI0YxLOMWVOkDgjc"
ssh-keyscan -t rsa $HOST > /tmp/hostkey
FINGERPRINT=$(ssh-keygen -lf /tmp/hostkey | cut -d ' ' -f 2)
if [ "$EXPECTED_FINGERPRINT" == "$FINGERPRINT" ]; then
  cat /tmp/hostkey >> ~/.ssh/known_hosts
fi
```

### Updating your display name
{: #git_update_name}

You can update the display name that appears for you throughout {{site.data.keyword.gitrepos}}.

1. On the [User Settings](https://us-south.git.cloud.ibm.com/profile){: external} page, in the **Main settings** section, update your full name.
1. Click **Update profile settings** to change the name that is displayed for you throughout {{site.data.keyword.gitrepos}}. 

## Physical file and repo size limits
{: #git_limits}

Files are strictly limited to 100 MB. The suggested repo size limit is 1 GB. If your repo exceeds 1 GB, you might receive an email with a request to reduce the size of the repo.

## Take a tutorial: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Check out one of these tutorials on the [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

   * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}. Learn how to create an open toolchain from a template and use the toolchain to continuously deliver a "Hello World" app.

   * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. Learn how to create a toolchain from a template with three microservices and use the toolchain to continuously deliver an online store.

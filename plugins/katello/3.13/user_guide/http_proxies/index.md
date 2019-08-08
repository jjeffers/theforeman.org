---
layout: plugins/katello/documentation
title: Http Proxies
version: '3.13'
---

# Http Proxies

## Http Proxy Support

Katello enables external http proxies (provided by utilities such as [squid](http://www.squid-cache.org/) for repository operations such as synchronization.

Http proxies can be created and then assigned to product though bulk selection as well as for each individual repository. Additionally, Katello provides http proxy policies for products or repositories. Policies include:
  * Using the global http proxy (the default)
  * Using a specified http proxy other than the global http proxy
  * Do not use any http proxy

## Creation

There are 2 ways of creating an Http Proxy for use in katello - through a rake task or though the Foreman UI.

### Creating an Http Proxy with Rake

bundle exec rake katello:update_default_http_proxy -- --name "A Great Http Proxy" --url "http://192.168.121.1:8888" --user admin --password redhat

> insert picture of command here <

### Creating an Http Proxy through the web UI

To create a new Http Proxy:

  - navigate to: Infrastructure > HTTP Proxies
  - click **New HTTP Proxy**

[pic of new proxy dialog]

- *Name*: This required option is used to identify the http proxy.
- *Url*: This required option is the URL of the proxy. Note that the scheme should be included. If the proxy uses a port, that must be incldued here as well. For example: "http://proxy.org:8888"
- *Username*: This option is used for proxy authentication, if required.
- *Password*: This option is used for proxy authentication, if required.

The provided field for **Test Connection** may be used to verify the proxy fields are set correctly. The field accepts a URL that a GET request will be sent to via the proxy configured in the form. If successful you will see a user notifcation such as:

[pic success proxy!]

If there is a problem with the proxy configuration, you will see an error notification similar to:

[pic failure!]

## Removal

To remove a Http Proxy:

  - navigate to: Infrastructure > HTTP Proxies
  - click **Delete** in the row of the proxy you wish to remove

## Setting the Global Default Content Proxy

If a Http Proxy exists you can specify a global default http proxy. Be default, newly created repositories will use this proxy for content synchronization requests.

To set the global default:

  - navigate to: Administer > Settings
  - click the **Content** tab
  - click the edit icon in the row labelled **Default http proxy** and select the proxy you wish to use as the default.

[pic content tab]

Note that selecting different http proxies will trigger updates to repositories that have the http proxy policy set to the the global default. Remote proxy settings will be updated asynchronously in a task.

## Bulk Applying Http



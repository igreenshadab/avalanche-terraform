---
description: Postman is a free tool used by developers to quickly and easily send REST, SOAP, and GraphQL requests and test APIs.
---

# Postman Collection

## What Is Postman?

Postman is a free tool used by developers to quickly and easily send REST, SOAP,
and GraphQL requests and test APIs. It is available as both an online tool and
an application for Linux, MacOS and Windows. Postman allows you to quickly issue
API calls and see the responses in a nicely formatted, searchable form.

We have made a Postman collection for Avalanche, that includes all the public
API calls that are available on [AvalancheGo
instance](./avalanchego-release-notes.md), allowing you to quickly issue
commands to your node and see the response, without having to copy and paste
long and complicated `curl` commands.

Along with the API collection, there is also the example Avalanche environment
for Postman, that defines common variables such as IP address of the node, your
Avalanche addresses and similar common elements of the queries, so you don't
have to enter them multiple times.

Combined, they will allow you to easily keep tabs on your node, check on its
state and do quick queries to find out details about its operation.

## Setup

### Postman Installation

Postman can be installed locally or used as a web app. We recommend installing
the application, as it simplifies operation. You can download Postman from its
[website](https://www.postman.com/downloads/). It is recommended that you sign
up using your email address as then your workspace can be easily backed up and
shared between web app and the app installed on your computer.

![Download Postman](/img/postman/postman-1-download.png)

After you installed the application, run it. It will prompt you to create an
account or log in. Do so. Again, it is not necessary, but recommended.

### Collection Import

Select `Create workspace` from Workspaces tab and follow the prompts to crate a new
workspace. This will where the rest of the work will be done.

![Create workspace](/img/postman/postman-2-workspace.png)

We're ready to import the collection. On the top-left corner of the Workspaces tab
select `Import` and switch to `Link` tab.

![Import collection](/img/postman/postman-3-import.png)

There, in the URL input field paste the link to the collection:

```text
https://raw.githubusercontent.com/ava-labs/avalanche-postman-collection/master/Avalanche.postman_collection.json
```

Postman will recognize the format of the file content and offer to import the
file as a collection. Complete the import. Now you will have Avalanche
collection in your Workspace.

![Collection content](/img/postman/postman-4-collection.png)

### Environment Import

Next, we have to import the environment variables. Again, on the top-left corner of the Workspaces tab
select `Import` and switch to `Link` tab. This time, paste the link
to the environment JSON:

```text
https://raw.githubusercontent.com/ava-labs/avalanche-postman-collection/master/Example-Avalanche-Environment.postman_environment.json
```

Postman will recognize the format of the file:

![Environment import](/img/postman/postman-5-environment.png)

Import it to your workspace. Now, we will need to edit that environment to suit
the actual parameters of your particular installation. These are the parameters
that differ from the defaults in the imported file.

Select the Environments tab, choose the Avalanche environment which was just added. 
You can directly edit any values here:

![Environment content](/img/postman/postman-6-variables.png)

As a minimum, you will need to change the IP address of your node, which is the value of 
the `host` variable. Change it to the IP of your node (change both the `initial` and `current`
values). Also, if your node is not running on the same machine where you
installed Postman, make sure your node is accepting the connections on the API
port from the outside by checking the appropriate [command line
option](../../nodes/maintain/avalanchego-config-flags.md#http-server).

Now we sorted everything out, and we're ready to query the node.

## Making API Calls

Open one of the API call groups, for example `Health`. Click `health` call:

![API call](/img/postman/postman-7-making-calls.png)

You will see that format of the call uses the `baseURL` environment 
variable. Click `Send`. Request will be sent, and soon you will see
the response, in the `Body` tab in the `Response`:

![Response](/img/postman/postman-8-response.png)

To see the actual call and the variables that are sent to the node, switch to
`Body` tab in the API call tabs. There you can quickly change the variables to
see the response to different queries.

## Conclusion

If you completed the tutorial, you are now able to quickly issue API calls to
your node without messing with the curl commands in the terminal. This allows
you to quickly see the state of your node, track changes or double-check the
health or liveness of your node.

## Contributing

We're hoping to continuously keep this collection up-to-date with the [Avalanche
APIs](./apis/README.md), and also add [data
visualizations](https://learning.postman.com/docs/sending-requests/visualizer/#visualizing-response-data).
If you're able to help improve the Avalanche Postman Collection in any way,
first create a feature branch by branching off of `master`, next make the
improvements on your feature branch and lastly create a [pull
request](https://github.com/ava-labs/avalanche-docs/pulls) to merge your work
back in to `master`.

If you have any other questions or suggestions, come [talk to us](https://chat.avalabs.org/).

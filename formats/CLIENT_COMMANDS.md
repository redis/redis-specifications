# Redis Client Library Command Specification

Redis client libraries provide helper functions for communicating with Redis. This specification exists to describe the format of the file used by redis clients, to communicate their function usage with Redis.

## Implementation

To implement this specification, a file named *usage.json* must be created at the root of the client repository. *usage.json* is a json formatted file containing links to generated documentation, and optionally examples.

The following is the basic example of the *usage.json* specification.

::
    {
      "name": "redis-py",
      "language": "python",
      "metadata": {
        "repository": "https://github.com/redis/redis-py",
        "issues_url": "https://github.com/redis/redis-py/issues"
      },
      "commands": {
        "SET": {
            "uri": "https://redis.readthedocs.io/en/latest/commands.html#redis.commands.core.CoreCommands.set",
            "examples": [
                {
                    "name": "Redis Set Example",
                    "description": "The following is an example of setting a key in redis.",
                    "example":  "import redis\nr=redis.Redis()\nr.set('foo', 'bar')",
                    "explanation": "In our example, a key named foo, is set to the value bar."
                }
            ],
            "added": "2.0",
            "history": [
                 {
                "version": "4.0.0",
                "note": "Added support for exat expiration flag",
                "releasenotes": "https://github.com/redis/redis-py/releases/tag/v4.0.0"
                }
            ]
        },
        "GET": {
            "uri": "https://redis.readthedocs.io/en/latest/commands.html#redis.commands.core.CoreCommands.get",
            "example": [
                {
                  "name": "Get Example",
                  "description": "The following is an example of retrieving a key named foo, already set in redis.",
                  "example": "import redis\nr = redis.Redis()r.get('foo')"
                }
            ],
            "added": "2.0"
        }
      }
    }

## Field Descriptions

* name - This is the name of client library
* language - The language of the client library

* metadata - A list of urls comprising of:
    * repository - A link to the source code for the Redis client library
    * issues_url - A link to open tickets for the client library

* commands - A map of commands, keyed to the redis command name, with links to their respective documentation.

    * uri - The link to the documentation for the associated redis command
    * examples *(Optional)* - A list of dictionaries, each comprising of an example of the function usage. Each dictionary contains the following elements:
        *  name - A name describing what the example does
        * description - A brief description of the example
        * example - A plain text entry containing the example. Newlines
        * explanation *(Optional)* - Text describing in depth, what the example does.

    * added *(Optional)* - The version of the client library containing this function
    * history *(Optional)* - A list of dictionaries containing change history. Each dictionary contains the following elements:
        * version - The client version containing this change
        * note - A plain text description of the change
        * release notes *(Optional)* - A link to release notes for specified client version

# Redis Client Library Command Specification

Redis client libraries provide helper functions for communicating with Redis. This specification exists to describe the format of the file used by redis clients, to communicate their function usage with Redis.

## Implementation

To implement this specification, a file named *functions.json* must be created at the root of the client repository. *functions.json* is a json formatted file containing links to generated documentation, and optionally examples.

The following is the basic example of the *functions.json* specification.

::
    {
      "name": "redis-py",
      "language": "python",
      "metadata": {
        "repository": "https://github.com/redis/redis-py",
        "issues_url": "https://github.com/redis/redis-py/issues",
      },
      "commands": {
        "SET": {
            "uri": "https://redis.readthedocs.io/en/latest/commands.html#redis.commands.core.CoreCommands.set",
            "example": [
                "import redis",
                "r = redis.Redis()",
                "r.set('foo', 'bar')",
            ],
            "added": "2.0",
            "history": [
                "4.0.0",
                "Added support for exat expiration flag",
                "https://github.com/redis/redis-py/releases/tag/v4.0.0",
            ],
        },
        "GET": {
            "uri": "https://redis.readthedocs.io/en/latest/commands.html#redis.commands.core.CoreCommands.get",
            "example": [
                "import redis",
                "r = redis.Redis()",
                "r.get('foo')",
            ],
            "added": "2.0",
        },
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
    * example *(Optional)* - A list of strings, comprising of an example of the function usage
    * added *(Optional)* - The version of the client library containing this function
    * history *(Optional)* - A list of changes.

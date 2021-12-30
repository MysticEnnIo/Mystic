# Mystic
Un bot Discord 
{
    "code": 50035,
    "errors": {
        "activities": {
            "0": {
                "platform": {
                    "_errors": [
                        {
                            "code": "BASE_TYPE_CHOICES",
                            "message": "Value must be one of ('desktop', 'android', 'ios')."
                        }
                    ]
                },
                "type": {
                    "_errors": [
                        {
                            "code": "BASE_TYPE_CHOICES",
                            "message": "Value must be one of (0, 1, 2, 3, 4, 5)."
                        }
                    ]
                }
            }
        }
    },
    "message": "Invalid Form Body"
}

{
    "code": 50035,
    "errors": {
        "access_token": {
            "_errors": [
                {
                    "code": "BASE_TYPE_REQUIRED",
                    "message": "This field is required"
                }
            ]
        }
    },
    "message": "Invalid Form Body"
}

{
    "code": 50035,
    "message": "Invalid Form Body",
    "errors": {
        "_errors": [
            {
                "code": "APPLICATION_COMMAND_TOO_LARGE",
                "message": "Command exceeds maximum size (4000)"
            }
        ]
    }
}

// Send
{
    op: 8,
    d: {
      guild_id: '308994132968210433',
      user_ids: [ '123123' ]
    }
  }
  
  // Receive
  {
    t: 'GUILD_MEMBERS_CHUNK',
    s: 3,
    op: 0,
    d: {
      not_found: [ 123123 ],
      members: [],
      guild_id: '308994132968210433'
    }
  }
  --boundary
  Content-Disposition: form-data; name="content"
  
  Hello, World!
  --boundary
  Content-Disposition: form-data; name="tts"
  
  true
  --boundary--
  --boundary
  Content-Disposition: form-data; name="payload_json"
  Content-Type: application/json
  
  {
    "content": "Bonjour tout le monde!",
    "embeds": [{
      "title": "Hello, Embed!",
      "description": "This is an embedded message.",
      "thumbnail": {
        "url": "attachment://myfilename.png"
      },
      "image": {
        "url": "attachment://mygif.gif"
      }
    }],
    "message_reference": {
      "message_id": "233648473390448641"
    },
    "attachments": [{
        "id": 0,
        "description": "Image of a cute little cat",
        "filename": "file.png"
    }, {
        "id": 1,
        "description": "Rickroll gif",
        "filename": "mygif.gif"
    }]
  }
  --boundary
  Content-Disposition: form-data; name="files[0]"; filename="file.png"
  Content-Type: image/png
  
  [image bytes]
  --boundary
  Content-Disposition: form-data; name="files[1]"; filename="mygif.gif"
  Content-Type: image/gif
  
  [image bytes]
  --boundary--

  {
    "embeds": [{
      "image": {
        "url": "attachment://screenshot.png"
      }
    }]
  }

  import requests


  url = "https://discord.com/api/v8/applications/<my_application_id>/commands"
  
  # This is an example Name commande or Slash Command, with a type of 1
  json = {
      "name": "Mystic",
      "type": 1,
      "description": "Send a Bot private",
      "options": [
          {
              "name": "bot",
              "description": "The type of Bot",
              "type": 3,
              "required": True,
              "choices": [
                  {
                      "name": "Random",
                      "value": "Bot_private"
                  },
                  {
                      "name": "ESport",
                      "value": "private_bot"
                  },
                  {
                      "name": "random",
                      "value": "bot_random"
                  }
              ]
          },
          {
              "name": "bot_random",
              "description": "send a bot random/private",
              "type": 5,
              "required": False
          }
      ]
  }
  
  # For authorization, you can use either your bot token
  headers = {
      "Authorization": "Bot <my_bot_token>"
  }
  
  # or a client credentials token for your app with the applications.commands.update scope
  headers = {
      "Authorization": "Bearer <my_credentials_token>"
  }
  
  r = requests.post(url, headers=headers, json=json)

  import requests


  url = "https://discord.com/api/v8/applications/<my_application_id>/guilds/<guild_id>/commands"
  
  # This is an example USER command, with a type of 2
  json = {
      "name": "random",
      "type": 2
  }
  
  # For authorization, you can use either your bot token
  headers = {
      "Authorization": "Bot <my_bot_token>"
  }
  
  # or a client credentials token for your app with the applications.commands.update scope
  headers = {
      "Authorization": "Bearer <my_credentials_token>"
  }
  
  r = requests.post(url, headers=headers, json=json)

  url = "https://discord.com/api/v8/applications/<my_application_id>/commands"
  
  # This is an example Name commande or Slash Command, with a type of 1
  json = {
      "name": "Mystic",
      "type": 1,
      "description": "Send a Bot private",
      "options": [
          {
              "name": "bot",
              "description": "The type of Bot",
              "type": 3,
              "required": True,
              "choices": [
                  {
                      "name": "Random",
                      "value": "Bot_private"
                  },
                  {
                      "name": "ESport",
                      "value": "private_bot"
                  },
                  {
                      "name": "random",
                      "value": "bot_random"
                  }
              ]
          },
          {
              "name": "bot_random",
              "description": "send a bot random/private",
              "type": 5,
              "required": False
          }
      ]
  }
  
  # For authorization, you can use either your bot token
  headers = {
      "Authorization": "Bot <my_bot_token>"
  }
  
  # or a client credentials token for your app with the applications.commands.update scope
  headers = {
      "Authorization": "Bearer <my_credentials_token>"
  }
  
  r = requests.post(url, headers=headers, json=json)

  import requests

  {
    "name": "permissions_test",
    "description": "A test of default permissions",
    "type": 1,
    "default_permission": false
}

MODERATOR_ROLE_ID = "<moderator_role_id>"
url = "https://discord.com/api/v8/applications/<my_application_id>/guilds/<my_guild_id>/commands/<my_command_id>/permissions"

json = {
    "permissions": [
        {
            "id": MODERATOR_ROLE_ID,
            "type": 1,
            "permission": True
        }
    ]
}

headers = {
    "Authorization": "Bot <my_bot_token>"
}

r = requests.put(url, headers=headers, json=json)

"name": "Mystic",
      "type": 1,
      "description": "Send a Bot private",
      "options": [
          {
              "name": "bot",
              "description": "The type of Bot",
              "type": 3,
              "required": True,
              "choices": [
                  {
                      "name": "Random",
                      "value": "Bot_private"
                  },
                  {
                      "name": "ESport",
                      "value": "private_bot"
                  },
                  {
                      "name": "random",
                      "value": "bot_random"
                  }
              ]
          },
          {
              "name": "bot_random",
              "description": "send a bot random/private",
              "type": 5,
              "required": False
          }
      ]
  }

  {
    "type": 2,
    "token": "A_UNIQUE_TOKEN",
    "member": {
        "user": {
            "id": "53908232506183680",
            "username": "random",
            "avatar": "a_d5efa99b3eeaa7dd43acca82f5692432",
            "discriminator": "1337",
            "public_flags": 131141
        },
        "roles": ["539082325061836999"],
        "premium_since": null,
        "permissions": "2147483647",
        "pending": false,
        "nick": null,
        "mute": false,
        "joined_at": "2017-03-13T19:19:14.040000+00:00",
        "is_pending": false,
        "deaf": false
    },
    "id": "786008729715212338",
    "guild_id": "290926798626357999",
    "data": {
        "options": [{
            "name": "name",
            "value": "The Gitrog Monster"
        }],
        "name": "cardsearch",
        "id": "771825006014889984"
    },
    "channel_id": "645027906669510667"
}

VALID

command
|
|__ subcommand
|
|__ subcommand

----

VALID

command
|
|__ subcommand-group
    |
    |__ subcommand
|
|__ subcommand-group
    |
    |__ subcommand

----

VALID

command
|
|__ subcommand-group
    |
    |__ subcommand
|
|__ subcommand

-------

INVALID

command
|
|__ subcommand-group
    |
    |__ subcommand-group
|
|__ subcommand-group
    |
    |__ subcommand-group

----

INVALID

command
|
|__ subcommand
    |
    |__ subcommand-group
|
|__ subcommand
    |
    |__ subcommand-group

    {
        "name": "permissions",
        "description": "Get or edit permissions for a user or a role",
        "options": []
    }

    {
        "name": "permissions",
        "description": "Get or edit permissions for a user or a role",
        "options": [
            {
                "name": "user",
                "description": "Get or edit permissions for a user",
                "type": 2 // 2 is type SUB_COMMAND_GROUP
            },
            {
                "name": "role",
                "description": "Get or edit permissions for a role",
                "type": 2
            }
        ]
    }

    {
        "name": "permissions",
        "description": "Get or edit permissions for a user or a role",
        "options": [
            {
                "name": "user",
                "description": "Get or edit permissions for a user",
                "type": 2, // 2 is type SUB_COMMAND_GROUP
                "options": [
                    {
                        "name": "get",
                        "description": "Get permissions for a user",
                        "type": 1 // 1 is type SUB_COMMAND
                    },
                    {
                        "name": "edit",
                        "description": "Edit permissions for a user",
                        "type": 1
                    }
                ]
            },
            {
                "name": "role",
                "description": "Get or edit permissions for a role",
                "type": 2,
                "options": [
                    {
                        "name": "get",
                        "description": "Get permissions for a role",
                        "type": 1
                    },
                    {
                        "name": "edit",
                        "description": "Edit permissions for a role",
                        "type": 1
                    }
                ]
            }
        ]
    }

    {
        "name": "permissions",
        "description": "Get or edit permissions for a user or a role",
        "options": [
            {
                "name": "user",
                "description": "Get or edit permissions for a user",
                "type": 2, // 2 is type SUB_COMMAND_GROUP
                "options": [
                    {
                        "name": "get",
                        "description": "Get permissions for a user",
                        "type": 1, // 1 is type SUB_COMMAND
                        "options": [
                            {
                                "name": "user",
                                "description": "The user to get",
                                "type": 6, // 6 is type USER
                                "required": true
                            },
                            {
                                "name": "channel",
                                "description": "The channel permissions to get. If omitted, the guild permissions will be returned",
                                "type": 7, // 7 is type CHANNEL
                                "required": false
                            }
                        ]
                    },
                    {
                        "name": "edit",
                        "description": "Edit permissions for a user",
                        "type": 1,
                        "options": [
                            {
                                "name": "user",
                                "description": "The user to edit",
                                "type": 6,
                                "required": true
                            },
                            {
                                "name": "channel",
                                "description": "The channel permissions to edit. If omitted, the guild permissions will be edited",
                                "type": 7,
                                "required": false
                            }
                        ]
                    }
                ]
            },
            {
                "name": "role",
                "description": "Get or edit permissions for a role",
                "type": 2,
                "options": [
                    {
                        "name": "get",
                        "description": "Get permissions for a role",
                        "type": 1,
                        "options": [
                            {
                                "name": "role",
                                "description": "The role to get",
                                "type": 8, // 8 is type ROLE
                                "required": true
                            },
                            {
                                "name": "channel",
                                "description": "The channel permissions to get. If omitted, the guild permissions will be returned",
                                "type": 7,
                                "required": false
                            }
                        ]
                    },
                    {
                        "name": "edit",
                        "description": "Edit permissions for a role",
                        "type": 1,
                        "options": [
                            {
                                "name": "role",
                                "description": "The role to edit",
                                "type": 8,
                                "required": true
                            },
                            {
                                "name": "channel",
                                "description": "The channel permissions to edit. If omitted, the guild permissions will be edited",
                                "type": 7,
                                "required": false
                            }
                        ]
                    }
                ]
            }
        ]
    }

    {
        "name": "Mystic",
        "type": 2
    }

    {
        "application_id": "775799577604522054",
        "channel_id": "772908445358620702",
        "data": {
            "id": "866818195033292850",
            "name": "context-menu-user-2",
            "resolved": {
                "members": {
                    "809850198683418695": {
                        "avatar": null,
                        "is_pending": false,
                        "joined_at": "2021-02-12T18:25:07.972000+00:00",
                        "nick": null,
                        "pending": false,
                        "permissions": "246997699136",
                        "premium_since": null,
                        "roles": []
                    }
                },
                "users": {
                    "809850198683418695": {
                        "avatar": "afc428077119df8aabbbd84b0dc90c74",
                        "bot": true,
                        "discriminator": "7302",
                        "id": "809850198683418695",
                        "public_flags": 0,
                        "username": "VoltyDemo"
                    }
                }
            },
            "target_id": "809850198683418695",
            "type": 2
        },
        "guild_id": "772904309264089089",
        "id": "867794291820986368",
        "member": {
            "avatar": null,
            "deaf": false,
            "is_pending": false,
            "joined_at": "2020-11-02T20:46:57.364000+00:00",
            "mute": false,
            "nick": null,
            "pending": false,
            "permissions": "274877906943",
            "premium_since": null,
            "roles": ["785609923542777878"],
            "user": {
                "avatar": "a_f03401914fb4f3caa9037578ab980920",
                "discriminator": "6538",
                "id": "167348773423415296",
                "public_flags": 1,
                "username": "ian"
            }
        },
        "token": "UNIQUE_TOKEN",
        "type": 2,
        "version": 1
    }

    {
        "name": "Mystic",
        "type": 3
    }

    "application_id": "775799577604522054",
    "channel_id": "772908445358620702",
    "data": {
        "id": "866818195033292851",
        "name": "context-menu-message-2",
        "resolved": {
            "messages": {
                "867793854505943041": {
                    "attachments": [],
                    "author": {
                        "avatar": "a_f03401914fb4f3caa9037578ab980920",
                        "discriminator": "6538",
                        "id": "167348773423415296",
                        "public_flags": 1,
                        "username": "ian"
                    },
                    "channel_id": "772908445358620702",
                    "components": [],
                    "content": "some message",
                    "edited_timestamp": null,
                    "embeds": [],
                    "flags": 0,
                    "id": "867793854505943041",
                    "mention_everyone": false,
                    "mention_roles": [],
                    "mentions": [],
                    "pinned": false,
                    "timestamp": "2021-07-22T15:42:57.744000+00:00",
                    "tts": false,
                    "type": 0
                }
            }
        },
        "target_id": "867793854505943041",
        "type": 3
    },
    "guild_id": "772904309264089089",
    "id": "867793873336926249",
    "member": {
        "avatar": null,
        "deaf": false,
        "is_pending": false,
        "joined_at": "2020-11-02T20:46:57.364000+00:00",
        "mute": false,
        "nick": null,
        "pending": false,
        "permissions": "274877906943",
        "premium_since": null,
        "roles": ["785609923542777878"],
        "user": {
            "avatar": "a_f03401914fb4f3caa9037578ab980920",
            "discriminator": "6538",
            "id": "167348773423415296",
            "public_flags": 1,
            "username": "user"
        }
    },
    "token": "UNIQUE_TOKEN",
    "type": 2,
    "version": 1
}

{
    "type": 4,
    "data": {
      "id": "816437322781949972",
      "name": "airhorn",
      "type": 1,
      "version": "847194950382780532",
      "options": [
        {
          "type": 3,
          "name": "variant",
          "value": "data a user is typ",
          "focused": true
        }
      ]
    }
  }

  FIRST_COMMAND_ID = "<first_command_id>"
  SECOND_COMMAND_ID = "<second_command_id>"
  ADMIN_ROLE_ID = "<admin_role_id>"
  
  url = "https://discord.com/api/v8/applications/<my_application_id>/guilds/<my_guild_id>/commands/permissions"
  
  json = [
      {
          "id": FIRST_COMMAND_ID,
          "permissions": [
              {
                  "id": ADMIN_ROLE_ID,
                  "type": 1,
                  "permission": True
              }
          ]
      },
      {
          "id": SECOND_COMMAND_ID,
          "permissions": [
              {
                  "id": ADMIN_ROLE_ID,
                  "type": 1,
                  "permission": False
              }
          ]
      }
  ]
  
  headers = {
      "Authorization": "Bot <my_bot_token>"
  }
  
  r = requests.put(url, headers=headers, json=json)

  {
    "content": "This is a message with components",
    "components": [
        {
            "type": 1,
            "components": []
        }
    ]
}

{
    "content": "This is a message with components",
    "components": [
        {
            "type": 1,
            "components": [
                {
                    "type": 2,
                    "label": "Click me!",
                    "style": 1,
                    "custom_id": "click_one"
                }
            ]

        }
    ]
}

{
    "version": 1,
    "type": 3,
    "token": "unique_interaction_token",
    "message": {
        "type": 0,
        "tts": false,
        "timestamp": "2021-05-19T02:12:51.710000+00:00",
        "pinned": false,
        "mentions": [],
        "mention_roles": [],
        "mention_everyone": false,
        "id": "844397162624450620",
        "flags": 0,
        "embeds": [],
        "edited_timestamp": null,
        "content": "This is a message with components.",
        "components": [
            {
                "type": 1,
                "components": [
                    {
                        "type": 2,
                        "label": "Click me!",
                        "style": 1,
                        "custom_id": "click_one"
                    }
                ]
            }
        ],
        "channel_id": "345626669114982402",
        "author": {
            "username": "Mason",
            "public_flags": 131141,
            "id": "53908232506183680",
            "discriminator": "1337",
            "avatar": "a_d5efa99b3eeaa7dd43acca82f5692432"
        },
        "attachments": []
    },
    "member": {
        "user": {
            "username": "Mason",
            "public_flags": 131141,
            "id": "53908232506183680",
            "discriminator": "1337",
            "avatar": "a_d5efa99b3eeaa7dd43acca82f5692432"
        },
        "roles": [
            "290926798626357999"
        ],
        "premium_since": null,
        "permissions": "17179869183",
        "pending": false,
        "nick": null,
        "mute": false,
        "joined_at": "2017-03-13T19:19:14.040000+00:00",
        "is_pending": false,
        "deaf": false,
        "avatar": null
    },
    "id": "846462639134605312",
    "guild_id": "290926798626357999",
    "data": {
        "custom_id": "click_one",
        "component_type": 2
    },
    "channel_id": "345626669114982999",
    "application_id": "290926444748734465"
}

// This is a message
{
    "content": "Mason is looking for new arena partners. What classes do you play?",
    "components": [
        {
            "type": 1,
            "components": [
                {
                    "type": 3,
                    "custom_id": "class_select_1",
                    "options":[
                        {
                            "label": "Rogue",
                            "value": "rogue",
                            "description": "Sneak n stab",
                            "emoji": {
                                "name": "rogue",
                                "id": "625891304148303894"
                            }
                        },
                        {
                            "label": "Mage",
                            "value": "mage",
                            "description": "Turn 'em into a sheep",
                            "emoji": {
                                "name": "mage",
                                "id": "625891304081063986"
                            }
                        },
                        {
                            "label": "Priest",
                            "value": "priest",
                            "description": "You get heals when I'm done doing damage",
                            "emoji": {
                                "name": "priest",
                                "id": "625891303795982337"
                            }
                        }
                    ],
                    "placeholder": "Choose a class",
                    "min_values": 1,
                    "max_values": 3
                }
            ]
        }
    ]
}

{
    "application_id": "845027738276462632",
    "channel_id": "772908445358620702",
    "data": {
        "component_type":3,
        "custom_id": "class_select_1",
        "values": [
            "mage",
            "rogue"
        ]
    },
    "guild_id": "772904309264089089",
    "id": "847587388497854464",
    "member": {
        "avatar": null,
        "deaf": false,
        "is_pending": false,
        "joined_at": "2020-11-02T19:25:47.248000+00:00",
        "mute": false,
        "nick": "Bot Man",
        "pending": false,
        "permissions": "17179869183",
        "premium_since": null,
        "roles": [
            "785609923542777878"
        ],
        "user":{
            "avatar": "a_d5efa99b3eeaa7dd43acca82f5692432",
            "discriminator": "1337",
            "id": "53908232506183680",
            "public_flags": 131141,
            "username": "Mason"
        }
    },
    "message":{
        "application_id": "845027738276462632",
        "attachments": [],
        "author": {
            "avatar": null,
            "bot": true,
            "discriminator": "5284",
            "id": "845027738276462632",
            "public_flags": 0,
            "username": "Interactions Test"
        },
        "channel_id": "772908445358620702",
        "components": [
            {
                "components": [
                    {
                        "custom_id": "class_select_1",
                        "max_values": 1,
                        "min_values": 1,
                        "options": [
                            {
                                "description": "Sneak n stab",
                                "emoji":{
                                    "id": "625891304148303894",
                                    "name": "rogue"
                                },
                                "label": "Rogue",
                                "value": "rogue"
                            },
                            {
                                "description": "Turn 'em into a sheep",
                                "emoji":{
                                    "id": "625891304081063986",
                                    "name": "mage"
                                },
                                "label": "Mage",
                                "value": "mage"
                            },
                            {
                                "description": "You get heals when I'm done doing damage",
                                "emoji":{
                                    "id": "625891303795982337",
                                    "name": "priest"
                                },
                                "label": "Priest",
                                "value": "priest"
                            }
                        ],
                        "placeholder": "Choose a class",
                        "type": 3
                    }
                ],
                "type": 1
            }
        ],
        "content": "Mason is looking for new arena partners. What classes do you play?",
        "edited_timestamp": null,
        "embeds": [],
        "flags": 0,
        "id": "847587334500646933",
        "interaction": {
            "id": "847587333942935632",
            "name": "dropdown",
            "type": 2,
            "user": {
                "avatar": "a_d5efa99b3eeaa7dd43acca82f5692432",
                "discriminator": "1337",
                "id": "53908232506183680",
                "public_flags": 131141,
                "username": "Mason"
            }
        },
        "mention_everyone": false,
        "mention_roles":[],
        "mentions":[],
        "pinned": false,
        "timestamp": "2021-05-27T21:29:27.956000+00:00",
        "tts": false,
        "type": 20,
        "webhook_id": "845027738276462632"
    },
    "token": "UNIQUE_TOKEN",
    "type": 3,
    "version": 1
}

@app.route('/', methods=['POST'])
def my_command():
    if request.json["type"] == 1:
        return jsonify({
            "type": 1
        })

        @app.route('/', methods=['POST'])
        def my_command():
            if request.json["type"] == 1:
                return jsonify({
                    "type": 1
                })
        
            else:
                return jsonify({
                    "type": 4,
                    "data": {
                        "tts": False,
                        "content": "Congrats on sending your command!",
                        "embeds": [],
                        "allowed_mentions": { "parse": [] }
                    }
                })

                import requests

                url = "https://discord.com/api/v8/interactions/<interaction_id>/<interaction_token>/callback"
                
                json = {
                    "type": 4,
                    "data": {
                        "content": "Congrats on sending your command!"
                    }
                }
                r = requests.post(url, json=json)

                const nacl = require('tweetnacl');

                // Your public key can be found on your application in the Developer Portal
                const PUBLIC_KEY = 'APPLICATION_PUBLIC_KEY';
                
                const signature = req.get('X-Signature-Ed25519');
                const timestamp = req.get('X-Signature-Timestamp');
                const body = req.rawBody; // rawBody is expected to be a string, not raw bytes
                
                const isVerified = nacl.sign.detached.verify(
                  Buffer.from(timestamp + body),
                  Buffer.from(signature, 'hex'),
                  Buffer.from(PUBLIC_KEY, 'hex')
                );
                
                if (!isVerified) {
                  return res.status(401).end('invalid request signature');
                }
                from nacl.signing import VerifyKey
                from nacl.exceptions import BadSignatureError
                
                # Your public key can be found on your application in the Developer Portal
                PUBLIC_KEY = 'APPLICATION_PUBLIC_KEY'
                
                verify_key = VerifyKey(bytes.fromhex(PUBLIC_KEY))
                
                signature = request.headers["X-Signature-Ed25519"]
                timestamp = request.headers["X-Signature-Timestamp"]
                body = request.data.decode("utf-8")
                
                try:
                    verify_key.verify(f'{timestamp}{body}'.encode(), bytes.fromhex(signature))
                except BadSignatureError:
                    abort(401, 'invalid request signature')

                    {
                        "id": "33590653072239123",
                        "name": "A Name",
                        "type": "twitch",
                        "account": {
                          "name": "twitchusername",
                          "id": "1234567"
                        }
                      }
                    {
                        "bot_public": false,
                        "bot_require_code_grant": false,
                        "cover_image": "31deabb7e45b6c8ecfef77d2f99c81a5",
                        "description": "Test",
                        "guild_id": "290926798626357260",
                        "icon": null,
                        "id": "172150183260323840",
                        "name": "Mystc",
                        "owner": {
                          "avatar": null,
                          "discriminator": "1738",
                          "flags": 1024,
                          "id": "172150183260323840",
                          "username": "i own a bot"
                        },
                        "primary_sku_id": "172150183260323840",
                        "slug": "test",
                        "summary": "This is a game",
                        "team": {
                          "icon": "dd9b7dcfdf5351b9c3de0fe167bacbe1",
                          "id": "531992624043786253",
                          "members": [
                            {
                              "membership_state": 2,
                              "permissions": ["*"],
                              "team_id": "531992624043786253",
                              "user": {
                                "avatar": "d9e261cd35999608eb7e3de1fae3688b",
                                "discriminator": "0001",
                                "id": "511972282709709995",
                                "username": "Mr Owner"
                              }
                            }
                          ]
                        },
                        "verify_key": "1e0a356058d627ca38a5c8c9648818061d49e49bd9da9e3ab17d98ad4d6bg2u8"
                      }

                      {
                        "name": "I am a role",
                        "id": 584120723283509258
                      }

                      {
                        "id": "41771983423143937",
                        "guild_id": "41771983423143937",
                        "name": "general",
                        "type": 0,
                        "position": 6,
                        "permission_overwrites": [],
                        "rate_limit_per_user": 2,
                        "nsfw": true,
                        "topic": "24/7 chat about how to gank Mike #2",
                        "last_message_id": "155117677105512449",
                        "parent_id": "399942396007890945",
                        "default_auto_archive_duration": 60
                      }

                      {
                        "id": "41771983423143937",
                        "guild_id": "41771983423143937",
                        "name": "important-news",
                        "type": 5,
                        "position": 6,
                        "permission_overwrites": [],
                        "nsfw": true,
                        "topic": "Rumors about Half Life 3",
                        "last_message_id": "155117677105512449",
                        "parent_id": "399942396007890945",
                        "default_auto_archive_duration": 60
                      }

                      {
                        "id": "155101607195836416",
                        "guild_id": "41771983423143937",
                        "name": "ROCKET CHEESE",
                        "type": 2,
                        "nsfw": false,
                        "position": 5,
                        "permission_overwrites": [],
                        "bitrate": 64000,
                        "user_limit": 0,
                        "parent_id": null,
                        "rtc_region": null
                      }

                      {
                        "last_message_id": "3343820033257021450",
                        "type": 1,
                        "id": "319674150115610528",
                        "recipients": [
                          {
                            "username": "test",
                            "discriminator": "9999",
                            "id": "82198898841029460",
                            "avatar": "33ecab261d4681afa4d85a04691c4a01"
                          }
                        ]
                      }

                      {
                        "name": "Some test channel",
                        "icon": null,
                        "recipients": [
                          {
                            "username": "test",
                            "discriminator": "9999",
                            "id": "82198898841029460",
                            "avatar": "33ecab261d4681afa4d85a04691c4a01"
                          },
                          {
                            "username": "test2",
                            "discriminator": "9999",
                            "id": "82198810841029460",
                            "avatar": "33ecab261d4681afa4d85a10691c4a01"
                          }
                        ],
                        "last_message_id": "3343820033257021450",
                        "type": 3,
                        "id": "319674150115710528",
                        "owner_id": "82198810841029460"
                      }

                      {
                        "permission_overwrites": [],
                        "name": "Test",
                        "parent_id": null,
                        "nsfw": false,
                        "position": 0,
                        "guild_id": "290926798629997250",
                        "type": 4,
                        "id": "399942396007890945"
                      }

                      {
                        "permission_overwrites": [],
                        "name": "Test",
                        "parent_id": null,
                        "nsfw": false,
                        "position": 0,
                        "guild_id": "290926798629997250",
                        "type": 4,
                        "id": "399942396007890945"
                      }

                      {
                        "id": "41771983423143937",
                        "guild_id": "41771983423143937",
                        "parent_id": "41771983423143937",
                        "owner_id": "41771983423143937",
                        "name": "don't buy dota-2",
                        "type": 11,
                        "last_message_id": "155117677105512449",
                        "message_count": 1,
                        "member_count": 5,
                        "rate_limit_per_user": 2,
                        "thread_metadata": {
                          "archived": false,
                          "auto_archive_duration": 1440,
                          "archive_timestamp": "2021-04-12T23:40:39.855793+00:00",
                          "locked": false
                        }
                      }

                      {
                        "reactions": [
                          {
                            "count": 1,
                            "me": false,
                            "emoji": {
                              "id": null,
                              "name": "🔥"
                            }
                          }
                        ],
                        "attachments": [],
                        "tts": false,
                        "embeds": [],
                        "timestamp": "2017-07-11T17:27:07.299000+00:00",
                        "mention_everyone": false,
                        "id": "334385199974967042",
                        "pinned": false,
                        "edited_timestamp": null,
                        "author": {
                          "username": "Mason",
                          "discriminator": "9999",
                          "id": "53908099506183680",
                          "avatar": "a_bab14f271d565501444b2ca3be944b25"
                        },
                        "mention_roles": [],
                        "content": "Supa Hot",
                        "channel_id": "290926798999357250",
                        "mentions": [],
                        "type": 0
                      }

                      {
                        "reactions": [
                          {
                            "count": 1,
                            "me": false,
                            "emoji": {
                              "id": null,
                              "name": "🔥"
                            }
                          }
                        ],
                        "attachments": [],
                        "tts": false,
                        "embeds": [],
                        "timestamp": "2017-07-11T17:27:07.299000+00:00",
                        "mention_everyone": false,
                        "id": "334385199974967042",
                        "pinned": false,
                        "edited_timestamp": null,
                        "author": {
                          "username": "Mason",
                          "discriminator": "9999",
                          "id": "53908099506183680",
                          "avatar": "a_bab14f271d565501444b2ca3be944b25"
                        },
                        "mention_roles": [],
                        "mention_channels": [
                          {
                            "id": "278325129692446722",
                            "guild_id": "278325129692446720",
                            "name": "big-news",
                            "type": 5
                          }
                        ],
                        "content": "Big news! In this <#278325129692446722> channel!",
                        "channel_id": "290926798999357250",
                        "mentions": [],
                        "type": 0,
                        "flags": 2,
                        "message_reference": {
                          "channel_id": "278325129692446722",
                          "guild_id": "278325129692446720",
                          "message_id": "306588351130107906"
                        }
                      }

                      {
                        "content": "@here Hi there from <@user>, cc <@user>"
                      }

                      {
                        "content": "@everyone hi there, <@user>",
                        "allowed_mentions": {
                          "parse": []
                        }
                      }

                      {
                        "content": "@everyone <@user> <@user>",
                        "allowed_mentions": {
                          "parse": ["users", "roles"],
                          "users": []
                        }
                      }

                      {
                        "content": "@everyone <@123> <@124> <@125> <@&200>",
                        "allowed_mentions": {
                          "parse": ["everyone"],
                          "users": ["1", "2"]
                        }
                      }

                      {
                        "content": "<@123> Time for some memes.",
                        "allowed_mentions": {
                          "users": ["1", "3"]
                        }
                    }

                    {
                        "content": "Hello, World!",
                        "tts": false,
                        "embeds": [{
                          "title": "Hello, Embed!",
                          "description": "This is an embedded message."
                        }]
                      }


                      {
                        "id": "41771983429993937",
                        "name": "LoL",
                        "roles": ["41771983429993000", "41771983429993111"],
                        "user": {
                          "username": "random",
                          "discriminator": "0002",
                          "id": "96008815106887111",
                          "avatar": "5500909a3274e1812beb4e8de6631111",
                          "public_flags": 131328
                        },
                        "require_colons": true,
                        "managed": false,
                        "animated": false
                      }

                      {
                        "id": null,
                        "name": "random"
                      }

                      {
                        "id": "41771983429993937",
                        "name": "LUL",
                        "animated": true
                      }
                      {
                        "id": "41771983429993937",
                        "name": null
                      }
                      {
                        "id": "197038439483310086",
                        "name": "Testers",
                        "icon": "f64c482b807da4f539cff778d174971c",
                        "description": "The official place to report Bugs!",
                        "splash": null,
                        "discovery_splash": null,
                        "features": [
                          "ANIMATED_ICON",
                          "VERIFIED",
                          "NEWS",
                          "VANITY_URL",
                          "DISCOVERABLE",
                          "MORE_EMOJI",
                          "INVITE_SPLASH",
                          "BANNER",
                          "COMMUNITY"
                        ],
                        "emojis": [],
                        "banner": "9b6439a7de04f1d26af92f84ac9e1e4a",
                        "owner_id": "73193882359173120",
                        "application_id": null,
                        "region": null,
                        "afk_channel_id": null,
                        "afk_timeout": 300,
                        "system_channel_id": null,
                        "widget_enabled": true,
                        "widget_channel_id": null,
                        "verification_level": 3,
                        "roles": [],
                        "default_message_notifications": 1,
                        "mfa_level": 1,
                        "explicit_content_filter": 2,
                        "max_presences": 40000,
                        "max_members": 250000,
                        "vanity_url_code": "testers",
                        "premium_tier": 3,
                        "premium_subscription_count": 33,
                        "system_channel_flags": 0,
                        "preferred_locale": "en-US",
                        "rules_channel_id": "441688182833020939",
                        "public_updates_channel_id": "281283303326089216"
                      }

                      {
                        "id": "41771983423143937",
                        "unavailable": true
                      }
                      {
                        "id": "197038439483310086",
                        "name": "Discord Testers",
                        "icon": "f64c482b807da4f539cff778d174971c",
                        "splash": null,
                        "discovery_splash": null,
                        "emojis": [],
                        "features": [
                          "DISCOVERABLE",
                          "VANITY_URL",
                          "ANIMATED_ICON",
                          "INVITE_SPLASH",
                          "NEWS",
                          "COMMUNITY",
                          "BANNER",
                          "VERIFIED",
                          "MORE_EMOJI"
                        ],
                        "approximate_member_count": 60814,
                        "approximate_presence_count": 20034,
                        "description": "The official place to report  Bugs!"
                      }

                      {
                        "enabled": true,
                        "channel_id": "41771983444115456"
                      }

                      {
                        "user": {},
                        "nick": "NOT API SUPPORT",
                        "avatar": null,
                        "roles": [],
                        "joined_at": "2015-04-26T06:26:56.936000+00:00",
                        "deaf": false,
                        "mute": false
                      }

                      {
                        "reason": "mentioning @user",
                        "user": {
                          "username": "@user",
                          "discriminator": "9999",
                          "id": "53908099506183680",
                          "avatar": "a_bab14f271d565501444b2ca3be944b25",
                          "public_flags": 131141
                        }
                      }

                      {
                        "description": "Discord Developers is a place to learn about Discord's API, bots, and SDKs and integrations. This is NOT a general Discord support server.",
                        "welcome_channels": [
                          {
                            "channel_id": "697138785317814292",
                            "description": "Follow for official Discord updates",
                            "emoji_id": null,
                            "emoji_name": "📡"
                          },
                          {
                            "channel_id": "697236247739105340",
                            "description": "Get help with Bot Verifications",
                            "emoji_id": null,
                            "emoji_name": "📸"
                          },
                          {
                            "channel_id": "697489244649816084",
                            "description": "Create amazing things with Discord",
                            "emoji_id": null,
                            "emoji_name": "🔬"
                          },
                          {
                            "channel_id": "613425918748131338",
                            "description": "Integrate Discord into your game",
                            "emoji_id": null,
                            "emoji_name": "🎮"
                          },
                          {
                            "channel_id": "646517734150242346",
                            "description": "Find more places to help you on your quest",
                            "emoji_id": null,
                            "emoji_name": "🔦"
                          }
                        ]
                      }

                      {
                        "name": "Flemme",
                        "type": 0
                      }

                      {
                        "name": "my-category",
                        "type": 4,
                        "id": 1
                      }
                      {
                        "name": "Flemme",
                        "type": 0,
                        "id": 2,
                        "parent_id": 1
                      }

                      {
                        "id": "2909267986263572999",
                        "name": "Test Server",
                        "icon": "389030ec9db118cb5b85a732333b7c98",
                        "description": null,
                        "splash": "75610b05a0dd09ec2c3c7df9f6975ea0",
                        "discovery_splash": null,
                        "approximate_member_count": 2,
                        "approximate_presence_count": 2,
                        "features": [
                          "INVITE_SPLASH",
                          "VANITY_URL",
                          "COMMERCE",
                          "BANNER",
                          "NEWS",
                          "VERIFIED",
                          "VIP_REGIONS"
                        ],
                        "emojis": [
                          {
                            "name": "ultrafastparrot",
                            "roles": [],
                            "id": "393564762228785161",
                            "require_colons": true,
                            "managed": false,
                            "animated": true,
                            "available": true
                          }
                        ],
                        "banner": "5c3cb8d1bc159937fffe7e641ec96ca7",
                        "owner_id": "53908232506183680",
                        "application_id": null,
                        "region": null,
                        "afk_channel_id": null,
                        "afk_timeout": 300,
                        "system_channel_id": null,
                        "widget_enabled": true,
                        "widget_channel_id": "639513352485470208",
                        "verification_level": 0,
                        "roles": [
                          {
                            "id": "2909267986263572999",
                            "name": "@everyone",
                            "permissions": "49794752",
                            "position": 0,
                            "color": 0,
                            "hoist": false,
                            "managed": false,
                            "mentionable": false
                          }
                        ],
                        "default_message_notifications": 1,
                        "mfa_level": 0,
                        "explicit_content_filter": 0,
                        "max_presences": null,
                        "max_members": 250000,
                        "max_video_channel_users": 25,
                        "vanity_url_code": "no",
                        "premium_tier": 0,
                        "premium_subscription_count": 0,
                        "system_channel_flags": 0,
                        "preferred_locale": "en-US",
                        "rules_channel_id": null,
                        "public_updates_channel_id": null
                      }

                      {
                        "id": "290926798626999250",
                        "name": "Test Server",
                        "instant_invite": "https://discord.com/invite/abcdefg",
                        "channels": [
                          {
                            "id": "705216630279993882",
                            "name": "random3",
                            "position": 2
                          },
                          {
                            "id": "669583461748992190",
                            "name": "random",
                            "position": 1
                          }
                        ],
                        "members": [
                          {
                            "id": "0",
                            "username": "random",
                            "discriminator": "0000",
                            "avatar": null,
                            "status": "online",
                            "avatar_url": "https://cdn.discordapp.com/widget-avatars/FfvURgcr3Za92K3JtoCppqnYMppMDc5B-Rll74YrGCU/C-1DyBZPQ6t5q2RuATFuMFgq0_uEMZVzd_6LbGN_uJKvZflobA9diAlTjhf6CAESLLeTuu4dLuHFWOb_PNLteooNfhC4C6k5QgAGuxEOP12tVVVCvX6t64k14PMXZrGTDq8pWZhukP40Wg"
                          }
                        ],
                        "presence_count": 1
                      }

                      {
                        "code": "randomMystic1369",
                        "uses": 2
                      }

                      {
                        "code": "hgM48av5Q69A",
                        "name": "random",
                        "description": "",
                        "usage_count": 49605,
                        "creator_id": "132837293881950208",
                        "creator": {
                          "id": "132837293881950208",
                          "username": "random",
                          "avatar": "79b0d9f8c340f2d43e1f78b09f175b62",
                          "discriminator": "0001",
                          "public_flags": 129
                        },
                        "created_at": "2020-04-02T21:10:38+00:00",
                        "updated_at": "2020-05-01T17:57:38+00:00",
                        "source_guild_id": "678070694164299796",
                        "serialized_source_guild": {
                          "name": "random",
                          "description": null,
                          "region": "us-west",
                          "verification_level": 0,
                          "default_message_notifications": 0,
                          "explicit_content_filter": 0,
                          "preferred_locale": "en-US",
                          "afk_timeout": 300,
                          "roles": [
                            {
                              "id": 0,
                              "name": "@everyone",
                              "permissions": 104324689,
                              "color": 0,
                              "hoist": false,
                              "mentionable": false
                            }
                          ],
                          "channels": [
                            {
                              "name": "Text Channels",
                              "position": 1,
                              "topic": null,
                              "bitrate": 64000,
                              "user_limit": 0,
                              "nsfw": false,
                              "rate_limit_per_user": 0,
                              "parent_id": null,
                              "permission_overwrites": [],
                              "id": 1,
                              "type": 4
                            },
                            {
                              "name": "general",
                              "position": 1,
                              "topic": null,
                              "bitrate": 64000,
                              "user_limit": 0,
                              "nsfw": false,
                              "rate_limit_per_user": 0,
                              "parent_id": 1,
                              "permission_overwrites": [],
                              "id": 2,
                              "type": 0
                            }
                          ],
                          "afk_channel_id": null,
                          "system_channel_id": 2,
                          "system_channel_flags": 0,
                          "icon_hash": null
                        },
                        "is_dirty": null
                      }

                      {
                        "code": "0vCdhLbwjZZTWZLD",
                        "guild": {
                          "id": "165176875973476352",
                          "name": "Random",
                          "splash": null,
                          "banner": null,
                          "description": "Very good description",
                          "icon": null,
                          "features": ["NEWS", "DISCOVERABLE"],
                          "verification_level": 2,
                          "vanity_url_code": null
                        },
                        "channel": {
                          "id": "165176875973476352",
                          "name": "random",
                          "type": 0
                        },
                        "inviter": {
                          "id": "115590097100865541",
                          "username": "random",
                          "avatar": "deadbeef",
                          "discriminator": "7653",
                          "public_flags": 131328
                        },
                        "target_type": 1,
                        "target_user": {
                          "id": "165176875973476352",
                          "username": "random",
                          "avatar": "deadbeef",
                          "discriminator": "1234",
                          "public_flags": 64
                        }
                      }

                      {
                        "topic": "The debate is over: diet is better than regular",
                        "participant_count": 200,
                        "speaker_count": 5 ,
                        "members": [
                          {
                            "roles": [],
                            "nick": "NOT API SUPPORT",
                            "avatar": null,
                            "premium_since": null,
                            "joined_at": "2015-04-26T06:26:56.936000+00:00",
                            "pending": false,
                            "user": {}
                          }
                        ]
                      }

                      {
                        "id": "840647391636226060",
                        "guild_id": "197038439483310086",
                        "channel_id": "733488538393510049",
                        "topic": "Testing Testing, 123",
                        "privacy_level": 1,
                        "discoverable_disabled": false
                      }

                      {
                        "id": "749054660769218631",
                        "name": "Random",
                        "tags": "wumpus, hello, sup, hi, oi, heyo, heya, yo, greetings, grweete, lcome, wave, :wave, :hello, :hi, :hey, hey, \ud83d\udc4b, \ud83d\udc4b\ud83c\udffb, \ud83d\udc4b\ud83c\udffc, \ud83d\udc4b\ud83c\udffd, \ud83d\udc4b\ud83c\udffe, \ud83d\udc4b\ud83c\udfff, goodbye, bye, see ya, later, laterz, cya",
                        "type": 1,
                        "format_type": 3,
                        "description": "Wumpus waves hello",
                        "asset": "",
                        "pack_id": "847199849233514549",
                        "sort_value": 12
                      }

                      {
                        "id": "847199849233514549",
                        "stickers": [],
                        "name": "Wumpus Beyond",
                        "sku_id": "847199849233514547",
                        "cover_sticker_id": "749053689419006003",
                        "description": "Say hello to Wumpus!",
                        "banner_asset_id": "761773777976819732"
                      }

                      {
                        "id": "80351110224678912",
                        "username": "Random",
                        "discriminator": "1337",
                        "avatar": "8342729096ea3675442027381ff50dfe",
                        "verified": true,
                        "email": "random@discord.com",
                        "flags": 64,
                        "banner": "06c16474723fe537c283b8efa61a30c8",
                        "accent_color": 16711680,
                        "premium_type": 1,
                        "public_flags": 64
                      }

                      {
                        "channel_id": "157733188964188161",
                        "user_id": "80351110224678912",
                        "session_id": "90326bd25d71d39b9ef95b299e3872ff",
                        "deaf": false,
                        "mute": false,
                        "self_deaf": false,
                        "self_mute": true,
                        "suppress": false,
                        "request_to_speak_timestamp": "2021-03-31T18:45:31.297561+00:00"
                      }

                      {
                        "name": "test webhook",
                        "type": 1,
                        "channel_id": "199737254929760256",
                        "token": "3d89bb7572e0fb30d8128367b3b1b44fecd1726de135cbe28a41f8b2f777c372ba2939e72279b94526ff5d1bd4358d65cf11",
                        "avatar": null,
                        "guild_id": "199737254929760256",
                        "id": "223704706495545344",
                        "application_id": null,
                        "user": {
                          "username": "test",
                          "discriminator": "7479",
                          "id": "190320984123768832",
                          "avatar": "b004ec1740a63ca06ae2e14c5cee11f3",
                          "public_flags": 131328
                        }
                      }

                      {
                        "type": 2,
                        "id": "752831914402115456",
                        "name": "Guildy name",
                        "avatar": "bb71f469c158984e265093a81b3397fb",
                        "channel_id": "561885260615255432",
                        "guild_id": "56188498421443265",
                        "application_id": null,
                        "source_guild": {
                          "id": "56188498421476534",
                          "name": "Guildy name",
                          "icon": "bb71f469c158984e265093a81b3397fb"
                        },
                        "source_channel": {
                          "id": "5618852344134324",
                          "name": "announcements"
                        },
                        "user": {
                          "username": "test",
                          "discriminator": "7479",
                          "id": "190320984123768832",
                          "avatar": "b004ec1740a63ca06ae2e14c5cee11f3",
                          "public_flags": 131328
                        }
                      }

                      {
                        "type": 3,
                        "id": "658822586720976555",
                        "name": "Clyde",
                        "avatar": "689161dc90ac261d00f1608694ac6bfd",
                        "channel_id": null,
                        "guild_id": null,
                        "application_id": "658822586720976555"
                      }

                      {
                        "op": 0,
                        "d": {},
                        "s": 42,
                        "t": "GATEWAY_EVENT_NAME"
                      }
                      {
                        "op": 10,
                        "d": {
                          "heartbeat_interval": 45000
                        }
                      }

                      {
                        "op": 11
                      }

                      {
                        "op": 2,
                        "d": {
                          "token": "my_token",
                          "intents": 513,
                          "properties": {
                            "$os": "linux",
                            "$browser": "my_library",
                            "$device": "my_library"
                          }
                        }
                      }

                      {
                        "op": 6,
                        "d": {
                          "token": "my_token",
                          "session_id": "session_id_i_stored",
                          "seq": 1337
                        }
                      }

                      {
                        "op": 2,
                        "d": {
                          "token": "my_token",
                          "properties": {
                            "$os": "linux",
                            "$browser": "disco",
                            "$device": "disco"
                          },
                          "compress": true,
                          "large_threshold": 250,
                          "shard": [0, 1],
                          "presence": {
                            "activities": [{
                              "name": "Cards Against Humanity",
                              "type": 0
                            }],
                            "status": "dnd",
                            "since": 91879201,
                            "afk": false
                          },
                          // This intent represents 1 << 0 for GUILDS, 1 << 1 for GUILD_MEMBERS, and 1 << 2 for GUILD_BANS
                          // This connection will only receive the events defined in those three intents
                          "intents": 7
                        }
                      }

                      {
                        "op": 6,
                        "d": {
                          "token": "randomstring",
                          "session_id": "evenmorerandomstring",
                          "seq": 1337
                        }
                      }

                      {
                        "op": 1,
                        "d": 251
                    }

                    {
                        "op": 8,
                        "d": {
                          "guild_id": "41771983444115456",
                          "query": "",
                          "limit": 0
                        }
                      }

                      {
                        "op": 4,
                        "d": {
                          "guild_id": "41771983423143937",
                          "channel_id": "127121515262115840",
                          "self_mute": false,
                          "self_deaf": false
                        }
                      }

                      {
                        "op": 3,
                        "d": {
                          "since": 91879201,
                          "activities": [{
                            "name": "Save the Oxford Comma",
                            "type": 0
                          }],
                          "status": "online",
                          "afk": false
                        }
                      }

                      {
                        "op": 10,
                        "d": {
                          "heartbeat_interval": 45000
                        }
                      }

                      {
                        "details": "Live Fortnite",
                        "state": "Rocket League",
                        "name": "Twitch",
                        "type": 1,
                        "url": "https://www.twitch.tv/tommydmg"
                      }

                      {
                        "name": "Rocket League",
                        "type": 0,
                        "application_id": "379286085710381999",
                        "state": "In a Match",
                        "details": "Ranked Duos: 2-1",
                        "timestamps": {
                          "start": 15112000660000
                        },
                        "party": {
                          "id": "9dd6594e-81b3-49f6-a6b5-a679e6a060d3",
                          "size": [2, 2]
                        },
                        "assets": {
                          "large_image": "351371005538729000",
                          "large_text": "DFH Stadium",
                          "small_image": "351371005538729111",
                          "small_text": "Silver III"
                        },
                        "secrets": {
                          "join": "025ed05c71f639de8bfaa0d679d7c94b2fdce12f",
                          "spectate": "e7eb30d2ee025ed05c71ea495f770b76454ee4e0",
                          "match": "4b2fdce12f639de8bfa7e3591b71a0d679d7c93f"
                        }
                      }

                      {
                        "token": "my_token",
                        "guild_id": "41771983423143937",
                        "endpoint": "smart.loyal.discord.gg"
                      }




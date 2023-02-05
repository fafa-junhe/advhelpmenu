# Advenced Help Menu
Advanced Help Menu for sourcemod, using json configs.
Menus can be paralleled or nested.

## Cvar
| name        | default                  | description      |
|-------------|--------------------------|------------------|
| advh_config | configs/advhelpmenu.json | config file path |

## Cmd
- sm_advhr reload helpmenu

## Requirements
- [sm-json](https://github.com/clugg/sm-json#error-handling) Compile only

## Config
- Note that shortcuts are chat triggers, use | to split, each menu can only have up to 10 shortcuts, and the maximum number of characters is 10, and those prefixed with / will be automatically hidden in the chat.
- maplist_name is the title of the maplist menu.
flags are the permissions required to enter the menu.
```json
{
	"advhelpmenu": [{
			"Help Menu": {
				"exit": "true",
				"type": "menu",
				"shortcut": "h|!h|!help|/help|help",
				"data": [{
						"Vip Menu": {
							"exit": "true",
							"flags": "o",
							"type": "menu",
							"shortcut": "vip|!vip|/vip",
							"data": [{
									"Fly": {
										"type": "text",
										"cmd": "say /fly"
									}
								},
								{
									"this text can't be clicked": {
										"type": "text"
									}
								}
							]
						}
					},
					{
						"List of Maps": {
							"type": "maplist"
						}
					},
					{
						"Thirdperson": {
							"type": "text",
							"cmd": "say /tp"
						}
					},
					{
						"Firstperson": {
							"type": "text",
							"cmd": "say /fp"
						}
					}
				]
			}
		},
		{
			"Admin Menu": {
				"exit": "true",
				"type": "menu",
				"flags": "abc",
				"shortcut": "/adm",
				"data": [{
					"Open Sourcemod Admin Menu": {
						"type": "text",
						"cmd": "say /admin"
					}
				},
						{
							"Open google": {
								"type": "motd",
								"url": "https://google.com"
							}
						}
				]
			}

		}
	],
	"maplist_name": "List of Maps"
}

```

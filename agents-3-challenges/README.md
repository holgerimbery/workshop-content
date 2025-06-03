# Workshop:  Develop Agents with Copilot Studio

by [@jenkra91](https://github.com/jenkra91) &amp; [@holgerimbery](https://github.com/holgerimbery) - Link: [https://ln.run/fJAFa](https://ln.run/fJAFa)

## start with the basics

![](./media/eeeb5023e5173e7e251c51c53823128058f27350.png)

- Please navigate to
  [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com/).

- Log in using your credentials.

- Switch to the correct environment by clicking on "Environment" in
  the top right corner (see picture above). Ensure that you select
  "copilotstudioinaday." Please do not use any other environment.

## Challenge 01: Travel Agent
- go to "Home" and use the "Safe Travel" template to begin.

![](./media/ae7fe25623434553a9e7a27a6df2a2d96040d018.png)

- please review all fields already provided with content,

![](./media/049b57c1e7a1de43f19335f69fe01be01ca2128e.png)

- Begin by renaming the Agent to "Safe Travels User0XX," where XX
  corresponds to your user number in this session.

- Please pay attention to the Instructions section; here, you will
  define your agent's purpose and communication style.

![](./media/3abe0bd29bfb04a876bd4d26963f0c58e9890a57.png)

- Next, scroll down to the Knowledge section. In this part, you will
provide your agent with its first capability, "Knowledge",

- This section is already pre-filled, but you may add an additional
website.

![](./media/5f868e65c0503762b4adaf3a9ce259f16de04ca4.png)

- Please add 
```
https://europa.eu/youreurope/citizens/
```
as a public website
and give it a helpful name.

![](./media/6e0b8768ca4e96b13dcfc85464859590968b0888.png)

- Press "Create" to start your first agent in this lesson.

![](./media/cb265f98a8bde80f4fdc22fa66aed6300cdd3596.png)

- Test your agent with examples and additional questions in the test
pane.

Test it with:

```
What is the US Visa Policy?

What visa do I need as an American citizen traveling to Europe?"
```

This agent serves as an excellent starting point for exploring Copilot
Studio.

You can incorporate web search functionality, select a different response model,
and include other elements you consider necessary.

## Challenge 02 - Develop an agent that can converse using your data from the beginning

- Close the first agent you created and return to the "Home" page.

- Use the conversational experience to create a new agent with the
following instructions: 
```
Create an agent to help answer questions about
and troubleshoot problems with Microsoft products.
```

![](./media/be3eba23e5d6c4c6b4394c110365855901183a75.png)

![](./media/47de3ec2c4e17035a10515c57fe028483ee90138.png)

- Continue the dialog and keep an eye on the instructions of the agents on
the right side.

- Change the name, please use "Microsoft Help Agent User0XX" as a name

- Give additional instructions, like

```
Don't talk about products or services that aren't Microsoft
```
```
Use a professional and friendly tone. For troubleshooting requests,
reply in bullet point format listing the steps to resolve
```

```
Add knowledge by asking to do so:

https://microsoft.com,

https://www.learn.microsoft.com,

https://developer.microsoft.com

```

- After adding the knowledge sources please confirm them by ticking them
on the right side:

![](./media/e3a08cc8e963cfde51ccedd290ad8b244149efdd.png)


- When ready, click on "Create" to initiate the second agent for your
session. Use the test pane to ask questions you have about Microsoft
products.

Examples:
```
How do I add an action to an agent in Copilot Studio?
```
```
How do I configure authentication in Copilot Studio?
```

## Challenge 03 - adding actions

- Please do not leave your agent, just stay where you are.

- Click on "Knowledge"

![](./media/6cad447f26f473d1c74a7549851296aed475306f.png)

- Then, click "+ Add Knowledge" and select SharePoint.

![](./media/b7113194c3ecd103e35db02e5262fed964493b90.png)

- add the following site: 
```
https://ddcoms.sharepoint.com/sites/IT
```


![](./media/f3b440b0336cf3bd442c166daec6cc1cd0257ed1.png)

* Go to Settings in the top right corner and check that generative
orchestration is enabled, if not do so.

![](./media/479d4d80527e565e0e15e2c68e2cf5b3f7e6aff5.png)


* Close this dialog with clicking on "X"
- go to topics, "+Add new topic" and "from blank"

![](./media/085ee76e8ac46087d841cea56eab1c5e365b0c4b.png)

- Enter the following text in the description of the topic:
```
This topic helps users find devices that are available from our
SharePoint device management list. They can ask to see available devices
and it will return a list of devices that are available which can
include laptops, smartphones, accessories and more
```

![](./media/ab549ce4c50cc82e6a6136d245fd2a2340ddff84.png)

- Click the plus button below the trigger

- Select add a tool

- Select the Connector tab

- Search for SharePoint get items

- Select the Get items -- SharePoint action

- If you do not have a connection here add one, otherwise select your
connection and click Submit

- Click the Site Address dropdown and select your site (as shown in the
picture)

- Click the List Name dropdown and select the devices list (as shown in
the picture)

![](./media/0d4e2b34f6296431a9e6fbed9fc0ce47e3e3be0f.png)

- Click the Select a variable option in the Output

- Select Create New

- Give the variable a name of ```VarDevices```

![](./media/6854a3434cde06a909f703d7dd3212f33fc8f55a.png)

- Select the add button between the trigger and "get items"

- Choose Ask a Question

![](./media/09fb47a6ac9a4339f7c1e64abdd57f1849aed4ca.png)

- Enter 
```
what type of devices are you looking for
```

in the question text

- Select multiple choice in the Identify dropdown

- Enter "Laptop" and "Smartphone" in the choice option

- Click the Save user response as

- Rename this variable to ```VarDeviceType```

![](./media/a3fb616117c78bb3ce5b36eee65d40def0c13f3c.png)

- Click the "add button" before the get items action

- Select "Variable Management"

- Select "Set a variable value"

![](./media/ac8e7b19a64cc06512bdeed5e89e1121a0608132.png)

- Choose the Select a variable dropdown

- Click Create a new variable

- Name this variable ```VarFilter```

- Choose the to value

- Select the Formula tab

- Paste in Power FX code reference in the talk track

```
Concatenate(\"Status eq \'Available\' and AssetType eq \'\",
Topic.VarDeviceType, \"\'\")\
```

![](./media/579912b229d1c337e702b24e2826cf0562018204.png)

- Select Insert

- Go to the action and expand advanced inputs

- Select the dropdown next to Filter Query

- Select ```VarFilter```

- Select the add button below the connector action

- Select send a message

- Click the Add button in the message

- Choose Adaptive Card

![](./media/54fdebfd0636511b60e1c805917aa7f860c59d95.png)

- Change the type to Formula

- Paste provided code

```
{ 
    type: "AdaptiveCard", 
    body: [ 
                { 
                    type: "TextBlock", 
                    text: "AVAILABLE DEVICES", 
                    wrap: true, 
                    size: "Small", 
                    isSubtle: true, 
                    weight: "Bolder", 
                    spacing: "Medium" 
                }, 
                { 
                type:"Container", 
                items:  
                    ForAll(Topic.VarDevices.value, 
                    { 
                    type: "ColumnSet", 
                    columns: [ 
                        { 
                            type: "Column", 
                            width: "80px", 
                            minHeight: "80px", 
                            items: [ 
                                { 
                                    type: "Container", 
                                    backgroundImage: { 
                                        url: Image, 
                                        horizontalAlignment: "Center", 
                                        verticalAlignment: "Center" 
                                    }, 
                                    minHeight: "80px", 
                                    horizontalAlignment: "Center", 
                                    verticalContentAlignment: "Center" 
                                } 
                            ], 
                            verticalContentAlignment: "Center", 
                            horizontalAlignment: "Left" 
                        }, 
                        { 
                            type: "Column", 
                            width: "auto", 
                            items: [ 
                                { 
                                    type: "TextBlock", 
                                    text: Model, 
                                    wrap: true, 
                                    weight: "Bolder", 
                                    size: "Medium" 
                                }, 
                                { 
                                    type: "TextBlock", 
                                    text: Manufacturer.Value, 
                                    isSubtle: true, 
                                    wrap: true, 
                                    spacing: "Small", 
                                     maxLines: 1 
                                }, 

                             { 
                                    type: "TextBlock", 
                                    text: "Color: " & Color.Value, 
                                    isSubtle: true, 
                                    wrap: true, 
                                    spacing: "Small", 
                                    maxLines: 1 
                                } 
                            ], 
                            verticalContentAlignment: "Center" 
                        }, 
                        { 
                            type: "Column", 
                            width: "20px", 
                            items: [ 
                                { 
                                    type: "Image", 
                                    url: "https://raw.githubusercontent.com/pnp/AdaptiveCards-Templates/main/samples/visual-list/assets/arrow-right.png", 
                                    horizontalAlignment: "Right", 
                                    width: "20px", 
                                    height: "20px", 
                                    selectAction: { 
                                        type:"Action.OpenUrl", 
                                        url:'{Link}' 
                                    } 
                                } 
                            ], 
                            verticalContentAlignment: "Center" 
                        } 
                    ] 
                } 
        ) 
        } 
    ] 
} 

```

- Click Save

- In the test window refresh and type ```What devices are there?```

So you have finished the 3rd part of this session.


Congrats!!!   
You made it!

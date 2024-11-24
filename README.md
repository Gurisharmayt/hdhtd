You have been provided with a transcript from a YouTube video on the N8N masterclass. Your task is to convert this transcript into a structured knowledge base focused on actionable points. This knowledge base will instruct an AI to build entire N8N workflows based on a single user idea. Follow these steps to complete the task:

1. The transcript content is provided below:



2. Begin by thoroughly reviewing the transcript to understand the content and identify key actionable points.

3. Extract actionable points that are relevant to building N8N workflows. These may include:
   - Step-by-step instructions for creating workflows
   - Key features and functionalities of N8N
   - Examples of workflows, AI agents, and backend processes
   - Tips for optimizing workflow efficiency
   - Troubleshooting common issues

4. Organize the extracted points into a structured format with clear headings and subheadings. Ensure that each section is logically ordered and easy to navigate.

5. Include information on all available N8N nodes and their functionalities. Ensure that examples of building workflows, AI agents, and backends are well-documented.

6. Use N8N documentation and internet resources to verify and enhance the accuracy of the information included in the knowledge base.

7. Write the entire structured and formatted knowledge base into a text file. Ensure that the file is well-organized and easy to read.

8. Review the final text file to ensure completeness, accuracy, and proper formatting.

Once you have completed these steps, the AI will have a comprehensive knowledge base to assist in building N8N workflows based on user requests.


```
today I'm going to be walking through

step by step how to build this super

simple question and answer AI agent like

it says right there no code basically

this agent is going to take information

you give it so information about a

company large database whatever it might

be and then you're going to be able to

chat with it to get the answers you need

quicker than if you were to manually

have to search through a document or

multiple documents so wanted to start

off here with just a quick demo so you

guys know what it's going to look like

and what it's going to do before we

actually get into the process of

building this thing so here is the

example that I'm using today it's a PDF

from Apple new features available with

iOS 18 that just came out so it's got a

ton of information here and if you

wanted to read all that be my guest but

I'm going to just build an agent that is

going to tell us the key highlights

basically so we get ask for highlights

or we could ask for a specific question

so in this case let's say um what is IOS

smart

reply it's going to search through that

exact PDF that I just showed you guys

and it's going to give us a nice concise

answer so let's see what we get here the

smart the iOS smart reply feature

assists user in quickly responding to

emails blah blah blah blah blah and the

mail app message app so it's a very

really quick summary it's very concise

and it's better than having to search

through here to find what we were

looking for which actually yeah anyways

so I just wanted to show you guys that

but let's just get into the rest of this

video let's see how we're going to build

this thing so the resources needed today

NN obviously that's where we're going to

be building the workflows to make this

agent pine cone this is the vector

database tool that I've been using um if

you don't really understand Vector

databases that's okay basically it is

just a way for agents to search through

large amount of data much quicker than

with a traditional relational database

or any other store that you might be

pulling information from

so Google drive this is just where the

PDF that I'm using is going to be pulled

from and then open AI API obviously just

to access that large language model of

open AI in order to

have the agent think and pull the right

information that we need and make it

concise and then as always with

everything in life just have a good

attitude okay so push data to Pine Cone

um that's going to be the first workflow

that we're doing today and then the

second one is going to be the actual

agent that's able to pull that data from

Pine Cone and give us an answer so let's

not waste any more time let's just get

straight into this one here um so yeah

the first step here would be grab some

sort of document that you want a PDF um

word anything but just push it into your

Google Drive so that we can access it

and then the next step is going to be

you need to set up a pine cone Index

this will take two seconds you're going

to go to Pine Cone you're going to click

here create new index the name can be

whatever just make sure you understand

what it was so anything mine is called

sample really all we need to configure

here is just going to be the model so

we're going to do text embedding three

small super simple that's all we need to

do you can play around with stuff as you

sort of

understand more about these databases

but for everything I do so far I've just

left it all default so you're going to

create that index I'm not going to do

that cuz I already have one like I said

mine is called sample and then we've got

our name spaces here so um if you watch

that last video about creating a simple

email AI agent um that's what this

contact name space is from but we're

going to be pushing it into a new one

we'll call it iOS or whatever but that

is basically going to be right here so

that's everything we really need to know

about pine cone for now and setting up

the the

database now we're going to get into

actually building this thing so the

first workflow I said that we were going

to be doing is um pushing the DAT into

pine cone so we're just going to call

this one push

data you're going to want to do trigger

manually is the the event that we're

going to use to trigger this workflow as

you can see there's all these different

options basically you need to select

what is going to start this workflow so

in this case if we click test workflow

that's what's going to start the process

of the data moving through so we've got

our trigger next we want to go

into these node selection and grab

Google Drive lots of actions here all we

need to do for this one is download the

file so when we test workflow it's going

to download this file and then we'll be

able to see it in in an

end okay so a lot of these stuff you're

going to have to configure um or sorry

get set set up with credentials if you

haven't done it yet so here's mine

basically for this Google Drive tool

you're going to click on create new

credential um you need to basically

enter a client ID in a client Secret in

order to let um NN know that it has

access to get into your drive or vice

versa but if you click open docs it's

going to be very super simple it's going

to walk you through exactly what you

need to do to get these credentials

you'll go here you'll create a cloud

account right here is mine you'll create

a project and then really easy you're

just going to go into enabled API and

services as you can see I have these

ones down here but you're just going to

click into here and you'll grab like

Google

Drive search for

that and then you'll see right here

Google Drive

API and all you have to do is enable it

so mine is already enabled but you'll

click a button right here that says

enable then you're going to go back

into into here you'll see credentials

you're going to create itial oo client

ID and then that is how you're going to

get your client ID and your secret I'm

not going to open up this right now but

that's basically where you'll find it so

you you'll copy and paste that into here

but then with this URL you have to make

sure that you set up your oo consent

screen so make sure you go in here and

set it up um this is just the one that I

have right now you're going to add

yourself as a test user otherwise you're

not going to have permission to go back

and forth basically or you can just

publish the the app so any of these

things um but when you're creating your

oo consent screen that is where you'll

be prompted it'll say like where is your

udirect redirect URL so that's exactly

what we're going to do and copy this

right here but if I didn't explain that

well enough like I said just click on

open docs and you'll see step by step so

go ahead and get that set up and then

you'll be prompted to sign in you should

be good to

go once you get all that set up you'll

be able to access your Google drive from

NN so right now we're going to be

grabbing the file type is a resource we

want to download it and then here we

have list URL or ID that's how it's

going to access the file it's really

nice that it has list because you can

come in here and just search for exactly

what oh exactly what file you want so

ours is the iOS one and we want the pdf

version um so then you can just test the

step here you'll be able to see exactly

like if it's working what the data looks

like as it's coming in so as you can see

it's coming in right here as binary and

then we want to just view it to make

sure that it it's the right PDF so this

is exactly what we were looking at

earlier so we're good to go the step is

working next we need to click on this

plus button right here and we want to

add the pine cone Vector store this is

going to allow us to push it into the

vector store so that we can later access

it so again you're going to have to set

up your credential it's going to ask for

an API key I already have mine set up so

I'm just going to click on that but

super simple again in Pine Cone right

here API keys and and you're just going

to copy this value so you'll just copy

that paste it into NN and again you'll

be good to go so operation here we don't

want to retrieve a document that might

be a later step but right now we want to

insert documents because we're getting

it from drive to Pine Cone again we're

able to choose from a list which is

super nice and that shows us that we

have been configured properly so sample

Index right here my index that we're

using over here is called sample so

that's good to go and then you have the

option here to add a namespace I am

going to add one just because it is

going to keep our

data more organized and it's easier to

call it it also will help the agent

figure out exactly what it's looking for

once you start to add you know tons of

different data into it but make sure

that it's actually connected from this

node to this

node and then next we need to set up a

couple more things with this Vector

store tool so first one we want to set

up this default data Lo keep that as

default and then I'm going to do

recursive to recursive character text

splitter um I'm going to leave the chunk

size is a th because the PDF is pretty

big the chunk size is basically how many

characters it's going to pull because

it's going to be pulling in batches from

the database and then the overlap is

just how many characters overlap between

chunks and I'm just going to leave that

as zero so going to go there and then we

just need to add the embedding to Pine

Cone so open Ai and then this is where

you'll set up the this credential I'm

pretty sure this is the last one so

again API key you'll go into open Ai and

you'll have your API keys right over

here on the side and then you're just

going to grab that key copy

it yeah the nice thing about it is once

you have everything set up they'll stay

set up so yeah you want to make sure

that this embedding is three small

because that's how we set up our pine

cone store and then um save that we

should be good to go so if we're going

to hit test workflow it's going to start

running we can see that it's going to

Google Drive it's grabbing our PDF then

it pushed it into pine cone successfully

I hope but we can go check right here

Nam space It should come through here as

iOS since that's what I named it let's

just refresh that

here oh no I know what happened

important step

so um right here default data loader we

had this as Json and we need to change

this to Binary because

if you remember over here this data came

through as binary if you go to Json

there's nothing showing up so make sure

that

this make sure you're aware of how your

data is coming through because in this

case nothing was being pushed into pine

cone because we didn't set up this

loader as binary data so we can leave

all that save Let's test it

again this should work

otherwise now I'm lost so okay we're

good to go Nam space it should push in

here there we go

iOS

perfect okay so we're done with this

workflow we're going to go back out

we're going to make a new one and then

this is going to be

our

Q&A agent okay the first step is again

what triggers this workflow this time

we're going to go on chat message

because we want to chat with this agent

to get it to work with

us leave that for now okay now we're

going to add in the actual entity of the

agent so click on this plus and we're

going to go down to Advanced

AI now you could do a question and

answer chain because that's essentially

what we want this agent to do but it's

good to get in the habit of setting

everything up through an AI agent

because then you're able to give it

access to more tools um more scenarios

that sort of thing so tools

agent um all of this can be the same and

eventually we need to add the system

message prompt I'm going to leave that

blank for now we'll prompt it near the

end but hopefully I don't forget cuz

sometimes I forget but that's the agent

the chat model we're going to use is

open AI we've already got that

configured I'm going to use

40 the memory we're going to give it is

Windows buffer memory we can leave

everything there it's going to have five

messages of contacts that it's going to

keep as we keep chatting it'll keep

saving the previous five messages in

order to look back and see like how the

conversation was going but we don't have

to touch anything really and that's just

a very simple easy way to give the agent

some sort of memory to have a

conversational

flow and then

tools so we're going to go and add pine

cone or vector store this is going to be

our

iOS um

information description you want to call

this tool to access information to

answer

the

users

questions just leave it as simple as

that okay

model open ashat model we pretty much

always do this and we always do 40 you

don't have to always do 40 I think uh 40

mini is a little cheaper uh 3.5 Works

they all work but 40 just is kind of the

most consistent I found so yeah then in

the vector store we want to add the pine

cone this is again

our

credential this time we want to retrieve

documents we're not inserting so we did

that earlier now we're retrieving and

then once again from list sample and

make sure if you pushed it earlier if

you push your data into a name space

over here so ours is an iOS make sure

that you call that namespace out again

otherwise your agent will be a little

lost okay so we got that set

up we do need to add the embedding right

here again

though um and this is going to be three

small cuz we've done three small

throughout every step so far okay save

that now okay I was about to say we're

going to test it but we need to prompt

it

because always forget that so this is

like I said you're able to take a

screenshot of your workspace and put

that in the chat and that's super useful

in order to actually prompt stuff so I'm

dragging in this one over here you can

see I did this earlier but let's just go

ahead and do that

again so there's that screenshot I'm

going to say prompt this agent to

answer questions

from from the

user we want to include jeez I cannot

type today include

background context and

instructions also

tell the agent to answer

concisely

okay so if you guys know stuff about

agents or at least a little bit about

agents if you know about prompting

prompting is super super important to

ensuring your agent is working

consistently and working exactly the way

you want it to a lot of times if it's

erroring it might be an issue just with

the prompting rather than an actual

thing you set up in the tools so this is

not the way I would advise to prompt

your agent um if they're complicated and

if it's like a big high stakes project

but when you're playing around with

making agents this quick way works super

well so background and context we've got

our models we've got our

tools um it's got instructions so let's

let's throw this in here and we'll test

it out and see see what see if we like

it or not okay and we'll save that so

let's see what we want to ask it

about let's ask

about what gen Emoji is since we're in

the AI space right

now what is IOS

18 gen

Emoji gen Emoji is a feature introduced

in iOS 18 that enables users to create

unique gen Emoji Style stickers directly

from the keyboard dog on a surfboard

cool um let's see what else can we ask

it let's go

can

you give a summary

of coolest features in iOS 18 this may

not work because I don't know how it's

going to well it probably will but it

needs to think about what does coolest

mean so let's see what it gives us

here oh wow the iOS 18 introduces

several Cutting Edge features designed

to enhance user convenience

accessibility and overall experience

experience here's a summary of the

coolest features eye tracking pretty

cool music haptics also pretty

cool wow yeah J Emoji's number seven on

the cool list I would say that's

probably top five but that's really not

what this video is about okay so that's

all that this agent going to be doing

for us today I know that it was pretty

simple but hopefully you understand all

the aspects of what goes into it all the

tools what they each do it's super

important to get that basic

understanding down because then you can

go in here and you can start adding more

tools and you can start calling more

workflows and then you can start pushing

data off of the agent or pushing data

from agent to a different agent so just

wanted to help give you guys a basic

understanding and if you enjoyed you

know please let me know what what else

you want to see um I'm going to try to

be tailoring a lot of Contour content

super step by- step um super easy to

follow and to beginners so if that

sounds like something that you enjoy

then definitely stick around but besides

that thanks guys

today I'm going to be walking through

step by step how to build this AI agent

in Ann no prior coding experience is

needed you'll be able to get this agent

up and running within 15 minutes so by

the end of it you'll have a great idea

of how to build Tools in NN and how to

have agents call different Tools in

order to be as effective as possible so

wanted to start off this video with a

quick demo of what this agent looks like

and what it's going to do here's what it

looks like it's okay if this doesn't

make sense by the end it all will you

can see the tools we have access to are

Wikipedia and the get weather tool this

is one that we create in nadn but let's

just chat with this agent to see how it

works so let's ask

it what is the capital of

Florida we get the capital of the US

state of Florida is Tallahassee if you

need any information about Tah has or

anything else feel free to ask so let's

say what

is the weather like there oops

misspelled there but it should be able

to be fine with

that the weather Tass is currently

partly cloudy with scattered clouds

temperatures warm 8.56 de F bit humid

blah blah blah gentle breeze blowing it

blah blah blah blah enjoy your day okay

awesome so that's sort of how it works

now let's go and get into actually

building this

thing so the resources needed here are

going to be nadn the weather API and

open AI API so this is just how we're

going to build the workflows how we're

going to access current weather

information and then open AI is just how

we're going to how the agent is going to

think and get the information and

formulate a response for us pretty

much so the workflows we're going to be

building today just two of them the

first one is the tool the git current

weather tool and then we'll be giving

the agent access to that tool and so the

second workflow is the AI agent yeah

let's just hop right into this one so

the first thing I would advise you do is

set up the open weather account um just

type in open weather map I think it

might be but you're going to want to set

this up and sign in or sign up as soon

as possible because your API key takes 5

to 10 minutes to actually process as um

valid so once you make your account

you'll go right in here click on my API

keys I'm going to disable this one after

the video because I'm exposed now but

your key will be right here or once you

uh verify your email they'll email email

you your key and they say within the

next couple hours but I found it usually

takes about 10 minutes so get that set

up and then we can hop into actually

building this thing so you don't have to

be sitting around

waiting okay so back to nadn okay so

we're going to add a new

workflow we're going to add the first

step so you always need to add a first

step when you build a workflow in NN

there's a lot of things that can trigger

a workflow you can trigger it manually

it can be on a schedule you can chat

with it we're going to do when called by

another workflow we're doing this

because when we talk to the agent and it

thinks oh I need to get weather

information

it's going to call this tool in order to

do that so that's how this one's going

to

execute now we're going to add a set

field edit field set we're going to

leave it as manual mapping and then

we're going to add a field here so let's

call this one city we can leave it as

string and then the value for now will

go Chicago just so that we can test if

the weather API is working but in the

end we're going to come back and fill

this in as a variable because the city

we're searching for is going to change

based on what we asked the

agent okay so we're good there now we

need to add the weather app so open

weather map we can either return current

weather data or return data for the next

5 days so this could be useful if we

wanted to build an agent that can do a

bunch of stuff with weather data but

let's just do current data for

now um this is where you're going to put

in your API key so this access token is

just the API key like I said in here um

go right there and paste that in so I

already did that obviously so not going

to do that current weather I'm going to

go Imperial format we can select a

location from this weather app based on

different things but we're just going to

stay with city name and then right here

is this is what city we're searching for

within the app so we're going to execute

this previous node and as we can see

from the set Fields node that we just

made we have the field of city with the

value of Chicago so if we drag this into

City this is going to change the search

the search in open weather map based on

what we typed into this field so we can

test the

step and now we can see this data that

came back so let's just go to table

format so it's easier to view oops so we

have weather clouds description we have

the

temperatures we have the wind we have

all this information and then we have

the name of the city that we search for

so just really quickly looking at the

data but we know that this not

worked so the next node we need to add

is an open AI

node lots of options here with an open

AI node that we can take but we're going

to go with message a

model okay so you're going to have to

connect um your open AI if you haven't

done that with a credential same exact

thing as open

Weather um just needs an API key so

you'll go into open AI if you haven't

made an account make one real quick and

then you'll just go to your API Keys

over here on the left create new key

name it whatever you want and then

create key and it will just give you the

option to copy your key and sorry paste

it right into here super simple all

right so we're going to keep it as text

message a model we're going to choose

the model so I'm going to choose

40 and now we need to give this a

message so what is this open Aon node

going to do so let me just paste this in

here real

quick so what we want to do is we want

to put the par below into a single query

field ensure it is a string so this is

the data that's coming back from open

weather map and now we need to put all

of this into one field so that the next

node can sort of interpret it and make

it into plain English English and so we

have troubles with this because a lot of

these are as you can see main for

example is a string because it has an A

but weather is a block or an object and

Main is an

object so we need to make sure that

these are all strings so the first thing

I'm going to do is we're going to start

making these parameters so

weather

description and then all we want to do

is drag in right here the

description okay actually let's go let's

make this full screen so you guys can

see this easier so we've got the

description and then over here it's

saying that weather description is

overclass clouds overcast clouds wow

okay so we've got description what else

do we want we want the temp and same

thing we'll find temp over here drag

that right in so it knows it's temp as

you can see over here it came in as

62.5 okay so I'm just going to do this

with a couple more variables here and

then I'll see you guys in a sec okay so

I only ended up doing three more just a

really concise look at what the

weather's like we've got weather

description temp humidity wind speed and

then what city we're in so we're going

to go here and now we just want to test

this step to make sure that it came out

correctly

Okay so we've got it

in a simple field although it came in a

little weird because it was called

content but this should work

fine it's got all the stuff we need and

it's in a string

so we'll be good here let's add another

um open AI node we're going to do the

same thing message a

model um all this is going to be the

same we're going to use 40 once again

and then this time we are going to say

convert the content field which is going

to be this one right here so convert the

content

field

um into simple

[Music]

English in a friendly

[Music]

tone we want

to use oh sorry I cannot type today use

emojis

to describe the weather okay so this one

is going to be a system prompt because

this is telling the opening I know what

to do we're going to add another message

this is where we're going to drag in

content and so this sees like what

exactly is going on down here it sees

the weather description everything we

just set up last node we'll keep it as

user and let's test the step to see what

comes

out so we get hey there here's the

weather update for Chicago it's mostly

cloudy with over overcast overcast Skies

the temperature is around 62 blah blah

blah so it it gave us the weather and it

put some emojis in there it's very

friendly um let's just throw in here

include

a

joke test it

again it's going to say looks like we're

in for some Cloudy Skies we got a bit of

a breeze going on too we don't fight

skeletons why don't skeletons fight each

other in the wind they don't have the

guts okay we'll leave that in there just

fun example so that threw in a joke so

we're pretty much done here because it

got what we needed as far as the weather

we pared it through and now we need to

add another set

field because we need to communicate

back to the agent hey we grabbed this

information and now here it is so you

can give it to the user that ask you the

question in the first place so manual

mapping once again we're setting a field

we're going to name this one response

it's going to be left as a string

and then for Value we're going to grab

content and put put that right in there

because this is just telling us exactly

what the agent or exactly what we just

read right so

awesome and now we can save

that let's call this

um get weather so this is our G weather

workflow and now we can go make the

agent so we're going to go

back add new

workflow um this is going to be

the

weather agent demo okay so first step um

back to the triggers I was talking about

earlier this one is going to be

triggered by a chat message because

we'll be talking to the agent so we've

got this next we want to add an an AI

agent so you can click on Advanced Ai

and then you've got the agent right here

so we're going to leave this as a tools

agent because it's going to be calling

in different tools prompts will'll take

it from the previous node and then

system message we will come back here in

a sec and prompt this agent exactly what

to

do so the chat model we need to use open

AI that's just the one I always go with

and I'm going to use 40 once

again we're going to give it a memory so

if you remember in the example I asked

the agent what's the capital of Florida

and then it came back and said the

capital of Florida and then I said can

you get me the weather for there or

what's the weather like there if we

didn't put in this this buffer memory

the agent wouldn't have remembered that

we just asked what the capital of

Florida was so it wouldn't know what

there was so I can show an example of

that near the end but this is important

just to give the agent some context of

what's going on and so that's what this

means it's like context window length

you can make it how many pass

interactions does the model receive as

context we're going to give it a quick

Wikipedia tool super simple you don't

even have to really set anything up this

is just giving the agent the ability to

search through

Wikipedia and then finally we want to

use call nadn workflow

tool this is where all the magic happens

because this is the tool that's going

to we're just going to call this one

weather once again weather so you have

to give it a description of when to use

this tool so very very basic call this

tool to access current weather

information going to go there we can

leave this as

database workflow from list you can

either do from list by ID but it's super

nice that they let you just choose from

a list of the workflows you've made so

we're going to use this is the one I

just made getor

weather and then the field to return is

response so if you remember at the end

we made that set field where we dragged

in the response from that last open AI

node and the field was called response

so that's how it knows what to say back

to us so we've got that there

I'll get to go so let's actually not

prompt this one because I want to show

you guys what it does when we just leave

it as helpful assistant it should be

fine because this is a pretty um simple

workflow but let's just go ahead and

give it a try

so what

is the weather like in

Denver we can see what's going on here

it grabbed the weather then it talked to

the model let's see what it said the

weather is currently cloudy with the

temperature of 62 blah blah blah so as

you can see might want to wear a light

jacket if you're heading out okay so it

gave us the weather but it didn't give

us the emojis that we asked for so we

can see exactly what happened here if we

go to all

executions save that real

quick we can see what happened in the

git weather

tool we can see exactly how the data

moved through to see if the workflow was

doing what we wanted it to

do so give this a second here as it

loads up

right here we see oh I know exactly what

happened exactly what I was worried of

we didn't change this back to a variable

so let's go back into that workflow and

make that a variable to make sure that

this is actually working

correct so get

weather now we need to change this to a

variable so if we put this in here as

json. query and make it an

expression then it knows that it's going

to

take whatever we chat and it's going to

put in the city

here okay so let's save this and try

that again now all right

so what is weather like in

Denver weather in Denver is currently

clear with temperature of 69 the

humidity is 39% okay so now let's make

sure it's

working is the weather like in Hawaii

just to make sure that it's actually

using different city names or state

names currently experiencing light rain

okay so it's working here here's a

little joke to brighten your day why did

the weather bring a ladder to work

because it wanted to rise the occasion

oh wow okay um so now let's test out the

Wikipedia node so what is capital

of Hawaii

so the capital of Hawaii is Honolulu and

now let me show you guys if we get rid

of this memory buffer save

that um what is the capital

of

Utah so remember earlier I was able to

say what's the weather like there what

is the weather like

there and now it shouldn't yeah see can

you please specify the location you want

to know the weather because it can't

remember that we just talked about

this so um yeah let's add that back in

here okay so I wanted to try one more

example so I can show you guys how the

data is moving through so let's just go

like what is the weather

in San

Diego so we've got the weather in San

Diego is currently experiencing

scattered clouds humidity level breeze

it's a great day to be outdoors okay so

we're going to go into all

executions and this is how we're able to

see exactly what happened in that get

weather

tool so we can see here um the city came

in as San Diego because it was a

variable it came through here got the

weather we parsed it it came out here

and if you've noticed this content is

not exactly the same that we got what

the agent said to us so this is probably

because of the way we prompted it so

let's go back in

here and I don't think it pulled up okay

so the prompt right now was just you're

a helpful assistant if we prompt it a

little more a little heavier it'll be

better with its response so this is not

the way that I would recommend prompting

especially when you get more tools you

always want to give it good background

good context you want to give it

specific instructions of how to use each

tool what the parameters in each tool

might be but for now let's just say you

are an

assistant used

to access weather information

anywhere around the world and so what we

want to do is make sure that it's giving

us all those emojis and the joke that we

asked for when we originally gave that

open AI node instructions

so please return

the response from

the get weather tool okay so we'll save

that and see what happens actually let's

go in here and just call it the weather

tool since that's what we called it

right here

so what is

the weather like in

Tokyo current weather in Tokyo features

broken clouds with a temperature of 72

there's a Brisk Breeze with wind speeds

around 17 okay so if you guys notice

that's still not giving us exactly what

would be coming out from here so let's

just refresh this we'll get that most

recent

execution

um so this is what the tool was giving

us at the end um as you can see there's

more emojis there's a little cloud or a

little joke at the end about

clouds and then here we didn't actually

get that full we didn't get the joke we

didn't get all the Emojis so this has to

do with prompting okay so I finally got

it working the way that we want it to be

working I asked how the weather is in

Spain hey there here's the weather

update for Spain gives a brief update um

it ends with a joke why did the weather

bring an umbrella because it wanted to

be a little shady stay comfy have a

great day so I found that it was

actually better to prompt the agent to

do um the jokes and the simple English

and the emojis in the actual agent

prompt rather than prompt prompting it

in the weather tool itself not sure

exactly why that is but prompting is

super super interesting and like I said

this isn't the way that you really

should be prompting a complicated agent

so if you guys are interested in a video

more about prompting let me know and I

can definitely try to work on that but

yeah that's pretty much what this agent

is going to do like I said you have the

ability to um ask information about

different different countries cities

whatever it may be and then ask about

the weather there so it's a simple agent

but it should open up your eyes to the

capabilities of Agents being being able

to call different tools being able to

search the web for different things and

just sort of how you can combine all of

that into one agent or multiple agents

that are able to call each other and

yeah I'm sorry for sort of the

interruptions in there in the middle or

sort of me forgetting to do things but

um I like to build these live so you

guys can sort of see the way that I

think through the flow of the data so

I'm going to continue to make sort of

step-by-step tutorials like this and try

to explain everything to the best of my

ability so if you enjoy this type of

cont content please let me know and yeah

that's it for now so thanks guys

all right everyone welcome to the nadn

AI agents Master Class I've been

building out AI agents in NN for a month

now and when I was first getting started

I remember being really confused on

configuring certain nodes and trying to

figure out when to use each one you know

I found myself getting stuck in my

workflows over the tiniest most specific

problems that were hard to find

tutorials on so in this video I'm going

to cover everything that I wish I'd

known from the start the tips the tricks

and answers that have taken me hours to

figure out so that you don't have to

spend that time like I did like I

mentioned this stuff can be really

confusing at first you've got all these

different AI nodes to choose from and

then once you click on a node you've got

all these different actions within each

node and then you have like AI agents

and when you click onto an AI agent

you've got different types of Agents

Within These agents and then you've got

different options you've got different

settings so by the end of this video all

of this will be much clearer to you and

you'll be more confident setting up more

sophisticated agent workflows if you

clicked on this video you probably

understand what AI agents are and sort

of how they work already but if not I'm

just going to go through really really

quick what they are and sort of how they

work so think of an AI agent as an

employee who has Perfect Memory follows

exact instructions never sleeps cost a

fraction of hiring a human and more so

don't want to oversimplify it we'll

leave it at this for now how do they

work essentially we have an entity so

think of an employee the human is the

entity and it has the brain and the

ability to think and reason and use

logic in order to use the tools that you

give it access to like Excel LinkedIn

Google word slack Google Drive that sort

of stuff so the entity is able to think

about which tool to use in order to get

a specific action done and so don't

oversimplify it it's the exact same

thing with an AI agent except for the

agent is the entity that has the ability

to think reason use logic and then it's

going to use the tools that you give it

access to in order to take action on

your behalf so first thing I wanted to

talk about is just the basics setting up

an AI agent workflow in nadn you can

pass information to an AI agent and you

can trigger in multiple ways and each

one is going to be suited to a specific

use case so as you can see in this

example we have um you know a Google

Sheets trigger we've got a webhook

trigger you can chat with it Gmail or

execute by other workflow um and

obviously this is just five examples

there's so many ways you can have agents

talk to each other or you can have

different triggers for an agent to you

know start doing its job but I just

wanted to quickly highlight this last

one real quick which is execute workflow

trigger this is basically saying that

this agent will start working when it's

called by another agent and um this is

super super powerful it lets you stack

and chain agents which allows you to

create super powerful multi-step

processes where each agent can focus on

a specific task passing data along the

chain so for example a conversational

agent could gather information from a

user pass it to a planning and execute

agent to create an action plan who would

then pass it to different tools agents

in order to take different actions you

know each tools agent specifies or

specializes in a different thing and it

can be passed around in order to do the

job

this approach lets you build really

sophisticated workflows where agents can

interact and collaborate in order to

achieve um objectives autonomously and

as they're doing so they're going to be

learning how to behave and getting

smarter at talking to each other and

sort of problem solving and real quick I

just wanted to plug my free school

Community the link for that will be down

in the description um couple benefits of

this are whenever I make a video on

YouTube pretty much I'll upload the

workflows on there so you can download

the NAD template and plug it right in

I'll have my prompts on there any code

Snippets I use will be on there as well

and then also just being able to have

discussions about um you know what's

going on in the AI space and if if you

want help troubleshooting stuff or you

want to collaborate there's um you know

a ton of like-minded people in there so

definitely feel free to join and I'll

see you guys in there okay now we're

going to sort of dive into that AI agent

node so this is what it's going to look

like um within ID end you'll click on it

and it will drag into your canvas and

then when you open it up to configure

the node you're going to see this where

you have to choose the type of agent as

you can see we've got tools

conversational open AI plan and execute

and then there are two more below this

so this is you know it can be

overwhelming you have to figure out what

is the goal of this agent which one

should I be choosing um all that kind of

stuff it can be confusing so that's what

we're going to talk about real quick

within nadn there are six types of

Agents you can choose from we've got a

tools agent conversational plan and

execute react SQL and then open AI

functions and to be honest I've only

been really using these main three so

we'll dive into these in the most detail

but I'll still talk about what these

ones do and when you should use them but

these are the three go-to that I always

use okay so the first one is a tools

agent this tools agent is a flexible

agent that can use external tools to

perform specific actions you can attach

different tools like calculators HTTP

requests um custom code you can allow it

to perform a variety of tasks and you

want to use this tools agent when you

need an AI agent to access other

applications or perform processes that

go beyond conversation such as calling

apis or doing calculations running

specific code or you know calling a

different workflow for example if you

want an agent that can receive user's

input look up information from a web API

and then send an email with all those

results the tools agent would be perfect

for this use case next we have a

conversational agent this one is

designed for human-like conversations

it's going to maintain context over

multiple interactions making it ideal

for something like a chatbot application

um you're going to want to use this one

when you want your agent to engage in

back and forth conversation with a user

like a chatbot that's going to remember

what the user said earlier and be able

to reference it and it will make more

sense then having a tools agent have no

idea of what's going on previous context

a perfect example of when you would want

to use a conversational agent would be

something like a customer support

chatbot that can answer questions keep

track of conversations context and

respond based on what the user

previously mentioned as if they were

talking to a human the third one we have

here is a plan and execute agent this

agent is going to be ideal for handling

complex tasks that need to be broken

down into steps it's going to plan out

what needs to be done and then execute

each step one by one you're going to

want to use use this agent when you have

a complex task that requires multiple

actions or stages or phases to complete

and you need each step to be executed in

sort of a structured organized sequence

great example of when to use a plan and

execute agent would be something like an

agent that helps with project planning

where it's going to break down a task

like organizing an event into individual

steps and it's going to execute each

step in order or send it off to a tools

agent to execute that step without

needing to remember previous steps so

it's was just going to take the plan and

execute and then for the other three

agents like I said I don't use these

ones too often but the first one's a

react agent this one is designed for

tasks that require reasoning and

deciding what actions to take based on

logic rather than conversation history

so it's good for situations where the

agent needs to think through a problem

um you could use this when you need an

agent to survey to analyze survey

responses to decide followup actions

something like that then we have the SQL

agent this one is a specialized agent

that can interface with SQL databases

it's going to translate natural human

language into to SQL queries which will

allow users to interact with it without

needing SQL knowledge in order to go get

stuff from a database so you obviously

want to use this when you want to

retrieve or manipulate data in the

database using natural language

especially if you're not familiar with

SQL and then finally we have the open AI

functions agent which is one that I

think is really cool and I definitely

want to start playing around with them

more but this one is going to leverage

open AI function calling capabilities

allowing the agent to select and execute

specific tools based on the requirements

of the task that you're giving it so

this agent is going to be really useful

when you need structured outputs from

open AI models as it can precisely pick

the right tool for you okay so now I

wanted to talk about JavaScript

variables and functions within NN

because this is something that's super

important to understand and when you

first get in there it may seem sort of

intimidating but it's really not so I

just want to break this down as simply

as I can so in NN we have variables and

these are this is just how data is going

to flow from one node to the next

especially when it's going to change

each time based on user input form

responses something like that and you're

able to reuse these variables and sort

of modify them so on the left here we

you can see the schema and this is just

something that you'll see how um agents

are inputting or outputting data we have

you know three different labels here

we've got the name Andrew Smith email

Andrew Smith gmail.com and then we have

the age and so the Json over here which

just stands for JavaScript object

notation it's a very simple way to

organize data um for humans and

computers to read and it's very very

commonly used so it's definitely

important just to be able to understand

what you're seeing here and it's not

that bad it's just key value pairs so

we've got the key of name Andrew Smith

is the value and same thing over here so

as you can see the similarities between

the Json and the

schema um and obviously this would be

changing each time so if you have 15

form responses these keys will be the

same and the schema over here the keys

will be the same but then the obviously

the actual values coming through will be

different based on which form you're

looking at now here's a live look at the

actual variables that you'll be seeing

within nadn so the example from the last

last slide with the schema we have the

name andreww Smith and his email and

what you would do is you take this right

here and you just drag it into a certain

field and then you'd see this is the

variable with the two curly brackets

dollar sign json. name and all that's

referring to is the name from the

previous node and then you'll see the

result come through so this would change

obviously like we just said for each

form or whatever it is how it's coming

through same thing with email json.

email we've got email up here so that's

how it's being referenced and we have

the result and like I said this will

change each time and we can reference it

later so that's why it's sort of you

know that green JavaScript variable and

if it's red it just means that it's not

valid um it's undefined so if you typed

email right here with a capital e um it

would not come through it would be R

because that's not exactly how it's

being referenced right here so

definitely wanted to throw that in there

cuz I remember one of my first agent

builds I was having a problem where it

was trying to read in um you know chat

input and the i in chat input was

supposed to be capitalized and I didn't

have it capitalized and it just wasn't

working and it couldn't read anything

and I was getting pretty flustered but

then I just realized okay well it's just

not being referenced correctly so make

sure that this is sort of being

referenced the same way that it comes

through okay now just one quick slide on

functions and like I said after this

we'll get into NN and I'll show some of

this actual live and I'll show the

dragon drop and it will make more sense

but functions are other ways that you

can have um things happen within

JavaScript so normally it's like json.

something if you're calling um you know

a v a variable from a previous node but

here we have actual functions Within

nadn so this is where it could seem a

little Cody but it's not too bad so one

thing that I was very confused about is

how do I get the agent to know the

current date and time and it's a super

simple function you just do the um two

curly brackets dollar sign now and as

you can see it's going to display the

current date and time right here and

then that's obviously not how you know a

computer can read this but a human

doesn't want to look at this so you can

dot format and then this will

automatically pop up and you can see it

displayed differently so this is like

the year the month and the day but you

can also edit this and you can change

how you want you could have it actually

say November you could actually have it

you know say the day in a different way

so I'll get in N Inn and show you guys

that in a sec but then um you can see

here's an example of different functions

so this one is if and you've got

conditions value of true value of false

almost similar to like an Excel

function but

um you really don't have to use these

too much because you're able to sort of

like use the large language model to

determine if you know value of true

value of false so you really don't have

to look at this it's nice that if you

type in two curly brackets it'll pull up

um sort of like a list of JavaScript

functions you have available to you and

it will sort of explain how to use them

but to be honest I hardly touch these I

really only use like now and I format

now so like I said let's hop in nnn and

just sort of look at this kind of stuff

all right we are now in Ann and I've

just set up a super simple agent it

really doesn't do anything but just

wanted to talk about um the JavaScript

variables and how they come in and out

of like an agent so in here we can see

this workflow would be executed by um a

different workflow and this is the PIN

data we have which was just in the

slides the name email and the age and

right now we're in the schema we can go

to table and we can see how simple it is

um and like I said if you had multiple

responses they'd be down here just like

a just like an Excel table with you know

column names and then the values and

then if you want to look at the Json

we've got um the name email and age so

you can kind of choose how you want to

see your data I usually go with schema

um because that's how you can actually

drag and drop this stuff and I'll show

you guys that in a sec but this is the

data that's coming through

and so then we open up the AI agent and

let's say that we wanted to have um The

Prompt is what we wanted to give him

this information and I'll I'll get more

into like what we're looking at in the

screen in a sec but for now this is what

we want and let's say that we wanted to

give this agent information about a

client so we said here is the client

information and then we'd go um name and

all we would do is we'd come over here

to name and we' drag in right here so as

you can see now that is a

um JavaScript variable it turned green

json. name it's referencing this and the

name is Andrew Smith we can do the same

for oops um we can do the same for email

and it's simple drag and drop with

schema we come in here json. email and

we get the email down here and then

finally we would be giving it the age

right here drag that in it's all green

we're all good and as you can see this

is the real information coming through

and this is just one item so if we had

15 it would be different for each one

but these variables would always be the

same so that's kind of the point of of

the variables okay now let's say we

wanted to you know give the agent

context of here is the current um you

know date and time so we just come in

here and if I type in the two curly

brackets we'll see the um JavaScript

functions available will pop up so

obviously this it looks pretty Cody like

I said I don't really touch this stuff

too much um but I could go to now right

here and that's how we're going to get

the current date and time and then like

I said if you type in do format and just

hit enter it's going to automatically do

this format for you so you can see it's

automatically done y y y- capital m

capital M and you get this is how you

get it back but let's say we didn't like

that um you could come in

here and so you can see how it changes

so now it's just the year but let's just

say if I did capital m capital M um now

we're getting no no now we're getting

November and um now we're just getting

an N you could come in here and do a

capital D you're getting the date like

that if you go again you'll get

something different you go again you'll

get that I'm not sure what we get there

now we even get the the day of the week

so let's say that's how we wanted the

agent to be able to understand what day

it is we would just do that and then

this variable would always stay the same

but this would change every single day

based on the time um that sort of stuff

so that's a really cool one um but then

like I said yeah you can just type this

in and you'll be able to see all it's

available to you you'll see sort of how

to configure it but um I don't touch

that because let's say we wanted to do

an if you know if the person's age is

greater than you know 20

so we would just say instead of doing a

function we could just say do you know

whatever it is if you want them to send

an email so send an email if

[Music]

um right here we just drag in if

age is greater than 25 and we could

leave that value hardcoded or we could

have that be a different variable but

it'd be coming through as like you know

let's actually just change this for the

sake of the video we would say oops we

would say only send an email if 32 is

greater than 25 and obviously we would

change it a little bit make it more easy

for the agent to actually understand

like if um Andrew Smith's email is

greater than 25 we would just have to

drag in the name and we could sort of

configure it right so um if Andrew

Smith's oops okay that's inside the

variable we just want to make sure it's

not inside the JavaScript

functions so we could just say like if

Andrew Smith's age

which is 32 is greater than 25 so I

don't know that's just a quick example

of how you could do it and why you don't

really need to use all these you know

Codi JavaScript functions but this now

one is definitely very useful and um

that's something that I had to figure

out okay now let's break down what we're

seeing here so obviously this is where

you choose the agent like we talked

about we have all these these six

different types and we talked about when

to use each one so right now we'll just

stay on a tools agent um and then we

have the prompt so you could either

Define below like we just did where you

talked to it or you could take from

previous node automatically which will

look for an input field called chat

input um and this is you know a lot of

times this is when you're actually

talking to the agent where you're using

chat message so um that's how that would

work and it would take like the chat

input field from over here json. chat

input or you could have it defined below

obviously so that's what we just did and

this is the prompt for the main

instruction or the question that the a

agent is going to respond to so this is

the direct command that that the agent

is expected to look through and act on

so that's a little different from like

an actual prompt this is kind of like um

its instructions for this use case but

then if you come down to options you

would go to system message and this is

where you actually want to give it um

the background the instructions how it

should behave the context this is where

you would set you know the tone

personality and um all the context of

like how it should act so this is like

it's instructions and then this is like

the current message so if like for

example The Prompt here was you are you

know a client onboarding agent and

you're going to take information from

the forms you're going to um run them

through the CRM you're going to email

them that sort of thing and then up here

we would actually just be feeding in the

information about the client so if that

makes sense um that's the difference

between like this prompt and then the

system message and so think of this as

like you know giving it the personality

and the job description down here so we

we've covered that system message

there's also other options we can look

at so we've got Max iterations um this

one is going to control how many times

the agent can go back and forth in a

conversational Loop so it's going to

limit how many turns the agent can take

in a conversation you probably want to

use this when you want to limit the

conversation length especially for use

cases where you want to avoid an endless

loop so an example of that would be if

you're setting it to three it means the

agent would only um try to reply up to

three times and then we have return

immediate steps so if you turn this one

on it is going to allow you to see all

the steps that the agent took to reach

its final answer and it's going to show

all of this immediately um after the

decision you want to enable this when

you want to help you know debug

troubleshoot figure out what's going on

when you want detailed transparency on

how the agent arrived at its answer and

you could look at the logs for that and

we'll get into logs later but it's

helpful to understand the flow of the

conversation and it can be really

helpful when you want to refine your

prompt and you want to see how you can

change it to make the agent act the way

you want it to and then the final option

down here is automatically pass through

binary images so when this one is

enabled it's going to take any binary

image images like image files or um you

know PDFs from a previous node and it's

going to automatically pass through the

AI agent node without being changed so

this is going to allow you to keep your

image files flowing through your

workflow alongside other data without

the AI agent trying to process it or

interpret it as plain text all right so

I haven't yet touched on require

specific output format I'll get back to

this in one sec but first I just want to

want to highlight how you know different

agents have different options so that

was tools conversational has the same

four options as you can see but if we go

to a plan and execute agent and we hit

add option it's just going to add this

it doesn't pull up that list of four

options so let's just quickly talk about

what a human message template does this

is just a way to guide the AI through

each step of a complex task so we talk

about how a plan execute agent will

break down a task into individual steps

and then work to execute those sort of

in order so this is like a script that

keeps the AI focused on what it's

already done what it needs to do now and

then any notes that um it needs to help

remember that process so um obviously

we' got previous step this is going to

be you know what it already has done and

so that it doesn't lose track of you

know where it needs to be and what it

needs to do next current objective

pretty much same thing this is what the

AI is focusing on right now and it's

going to keep it focused on executing

this task without getting distracted by

other data or other steps that are

coming through so it's just going to be

a clear instruction and then the scratch

Pad just a space where the AI can sort

of jot down any information

that it might need later it might need a

reference back later um and usually the

best case for when you're using a plan

and execute agent is to not touch this

stuff you can pretty much just leave it

as is this was already hardcoded into

this agent configuration so I would just

leave this as is um I've tried to play

around with it before and it kind of

just doesn't really add any value and it

even makes it mess up more so just leave

this as is because it's just going to

take what it's already done what it's

doing now and then write down notes and

stuff like that so that's what this

option does does okay and now we have

the settings tab and this one is pretty

much the same for all different types of

Agents conversational tool plan and

execute so the first thing we have is

always output data this is going to

ensure that um the node outputs data

even if it didn't execute a specific

action so you want to enable this if you

want the workflow to keep flowing

regardless of whether the AI agent

returned a result or not then we have

execute once so when this one's turned

on it's going to restrict the agent to

only running once during the workflow

you want to use this to prevent the

agent from being triggered multiple

times which is helpful for controlling

execution in Loops or repetitive tasks

stuff like

that then we have retry on fail so when

you're using this one um it's going to

automatically retry running the agent if

it fails the first time so you'll use

this to enable it for scenarios where

you may have like network issues or

temporary errors that may cause a

failure so it's going to allow your

agent to continue retrying before it

gives up and obviously you can you can

set up how many times you want it to try

and um wait between tries and stuff like

that so that's how you can kind of be in

control of its retrying and then you can

set up what you want it to do on air so

the default option is that it's just

going to stop the workflow um even if

there's stuff after the agent it's just

going to stop but you can choose to have

it continue so if you do this obviously

it's going to um just pass an error

message through but another cool way to

do it is continue using an error output

so um this will sort of break off two

different branches off of the agent so

as you can see there's a success branch

and an error Branch so this is cool

because if it's working successfully you

could have the um agent continue going

down this logic over here but if it

doesn't work then you could have the

agent um you know send some sort of

email saying that it didn't work or you

could have it um respond to the agent

saying you know what the error was so

this is a cool way to sort of um have

that air handling built in but as you

can see if you turn that off in settings

just with the stop or continue we'll do

continue it's going to take away that

branch and so now we only have one

option to to go through no matter what

so um that is just another cool way to

make the agents more powerful and

smarter and then back in the settings

for this agent we have notes so um I

used to think that this was something

like within a prompt where you could

tell the agent very specific things on

how to ask on how to act like I like

saying please answer in all caps or

something like that but that's not the

case this is pretty much just notes for

you to remember stuff about this agent

or for if you're collabor collaborating

with someone on this workflow like if I

said um prompt needs refining that's

just notes for me and my team to look at

and then you could also display the note

inlow so then it would just come right

here prompt needs refining but if we

turn that off then it will just say um

like plan an execute agent so that's

that's what it is and it has nothing to

do with the actual um way that the agent

will act or the way that it's in you

know taking in data it's just for you to

see pretty much okay now the last thing

I wanted to touch on is the require

specific output format because we didn't

talk about this so if I turn this off

off um we only have the tool option at

least for this agent um a conversational

or a tools one would have the memory as

well but we just have tools now we turn

this back on it's going to say connect

an output parser to the canvas to spec

specify the output format you require

and as you can see now we have an output

parser over

here um so yeah pretty much this is just

going to allow you to control the format

of your response that you receive from

the AI when it's enabled it's going to

have you specify exactly how the output

should be structured such as if you

require it to be in a particular format

you know a particular Json format so

that you can pass it through into the

next Fields um but it will just let you

list or you know specify the structure

that you want from the agent when it

goes off this way um so if you click an

Alpa parser you have three options autof

fixing item list and structured output

parser and let's just hop back into the

slides real quick in order to talk about

these things all right so output parsers

we very briefly touched on it but I just

want to reiterate the two reasons you

want to use them for consistency and for

reliability so it's going to ensure that

your ai's response is in a predictable

structure helpful for workflows that

need to process the output in a specific

way and it's also going to make it

easier to handle and pass data to other

nodes after your agent in the workflow

since you know the format is going to

match exactly what you specified so the

first one we have here is an autof

fixing output parser um this one is

going to automatically adjust the output

if it's not in the expected format this

one will use um some sort of large

language model to look at and fix by

itself

and this is good for when you need the

flexibility but you still want reliable

formatting because the parser is going

to sort of fix the response in to fit

the required structure then we have the

item list output parser this one is

going to separate the output into

individual items so you would use this

when you're expecting to get a list back

of results and you want each item to be

handled separately like multiple rows

within a spreadsheet and then finally we

have the structured output parser which

is going to force the output to follow

some sort of strict Json structure that

you fine in that output parser so for

example um like the stuff we were

looking at earlier with the name and the

email you could have you know you could

have the Json put in there in a very

specific structure with name email age

and then it will always come through

from that agent matching those those uh

keys to those values if that makes sense

okay back in nadn now I just wanted to

show what it looks like when you

actually attach these different output

parsers so um obviously we talked about

what these do and so wanted to show this

because it may be a little confusing

when you add the autof fixing one um you

can see that you have to add a chat

model obviously so we'll connect this

real quick but then also you see that

you need to add some sort of output

parser so in here once again it opens up

the same output parser so um you know we

choose from list or structured and this

is kind of confusing because it's like

why would you add this here if you could

just add um you know this structured one

right away and so that's like what was

going through my mind basically it's

going to be more flexible because the

autof fixing one is going to correct any

small formatting errors with the AI

response first of all because the AI

occasionally will return data that's

almost but not quite in the required

format to feed straight into the

structured output parser um and so after

the autof fixing step the structured

parser will confidently enforce the Json

format that we had you know specified

with less errors than if we had just

connected this straight away to the

agent and so basically it's just an

extra step right here to make sure that

the agents respond

is being fed in properly because we want

it to come through as you know specific

Json right here is State and cities and

as you can see it would sort of list out

the stuff correctly um and if we were to

do the item list um this one doesn't

even really need to be configured but

once again just wanted to sort of lay

that out because I was always thinking

why would I even add that autof fixing

one and have it connect to a large

language model if I could just throw in

the Json right here but hopefully that

made sense and that's why you would do

it like that okay now we're going to be

doing just a live build of an AI agent

in nadn we're just going to build out a

really simple one give it access to a

few tools and just to show some of the

aspects of looking at the agent logs um

looking at memory seeing the differences

in prompting and how that's going to

work so we're just going to do a simple

agent here our trigger is going to be on

chat message because we will be chatting

with this agent in NN just right here in

this chat window obviously we talked

about some of the triggers you can

connect it to um you know your SMS if

you wanted to text that you could have

it on Gmail or if you want to talk to it

through some sort of website or

different app obviously you can trigger

there but we're doing just chatting with

it in NN and we're going to go into the

next node and grab an advanced AI

obviously a ton of AI nodes we'll talk

about these ones later but just wanted

to show a quick agent build so we're

going to grab an AI agent we're going to

leave this one as tools and we will

configure this stuff in a sec after we

give it access to some other stuff so

the first thing obviously is to connect

a chat model sort of the brain um it

will think about what we said based on

this chat model so we'll come in here

and click um we'll take 40 and as you

can see we got this right here so it'll

think about what we say and then it will

hit the chat model and then go back to

the agent in order to interpret what we

asked and to figure out which tools to

send it off to so before we add tools um

we're going to go with the window buffer

memory this is sort of the NN builtin

one it's super easy to configure because

you don't even have to but we've got

other options for memory we've got

postgress um you can use all this other

stuff but going to use window buffer

memory here going to leave it as is

leave it as five context window length

and basically when we're chatting with

it in NN it'll remember five of our past

interactions and it can see how it

answered and it can see what we're

referencing um and I'll I'll show a live

example of using this and then I'll show

where we take it out and we'll see but

that is how that works and it's super

easy to configure and we just throw that

in there and so for tools we are just

going to grab a simple Wikipedia tool

right here don't even have to configure

that one one and then we'll grab a

calculator as well don't have to

configure that one and then obviously

this is where you would be able to um

call some sort of nadn tool so let's say

this agent was supposed to be helping

send emails we could choose from

workflow and I could grab like a send

email tool right here so I could

configure this one have it set up right

here and then when it figures out it

needs to send an email it would hit this

tool because it's referencing a

different workflow that goes through

logic to send an email so we'll get rid

of this for now but that is just sort of

how that could work and super cool

stuff so these are just the tools that

we're going to give it access to in the

model and the

memory and now we need to see what goes

on in here so we don't need to require a

specific output format we'll leave it as

a tools agent and I'll switch this later

to conversational and we can sort of see

the difference but the prompt right now

is going to be taken from the previous

note automatically it's going to be

looking for a field called chat input so

once we chat with it um the field of our

query whatever we type in will be right

here under you know a Json key or schema

of um chat input or it'll be json. chat

input but I'll show you guys that in a

sec so we've got that and then we have

um a system message so right now it's

just going to say you're helpful

assistant we'll save it as that and then

we'll ask what is the capital of

Illinois it will so it's going to go

through here it's going to store it in

the memory and then let's see what it

said it told us the capital of Illinois

is Springfield so now we can go into the

log we can look right here actually so

the first thing that it did was it

received our message and then it updated

in the window buffer memory what is the

capital of Illinois it ran through its

prompt and how to format and then it hit

the open AI

model um the capital what is the capital

of Illinois we can see the input and it

actually just answered from this model

so that's pretty cool because it didn't

even have to reference the Wikipedia

node so we'll do one where it has to

reference that to show that but um then

it finally just updates the response in

the window buffer memory so you can see

it this is what we asked what's capital

Illinois and then it responded the

capital of Illinois Springfield so then

I could reference it again and just say

like what about um

Florida and it will know that we're

asking about the capital because we just

pretty much talked about that so the

capital of Florida is Tallahassee if we

were to remove this window buffer memory

so now it has no context and I said what

about um California it's probably not

going to give us the capital it's going

to say could you please specify what

you'd like to know about California see

um that's sort of how that works but

yeah so we'll add this memory back in

here um right here just going to go back

in

here and now what we should try is um

we'll see the difference in a prompt so

helpful assistant is good but now let's

say you should always

respond very friendly and use joke

and emojis okay so that's super simple

prompt obviously that's not how you

prompt I want to make a video on

prompting so if that's something you

guys interested in please let me know

but now we will see if we ask another

question so like um what is or like can

you um what does the

company Nike do it will search Wikipedia

for Nike and then it will give us the

information and it should do it friendly

maybe a joke or two in there with Emojis

so Nike is this like the superhero of

the sportsware world Emoji they are the

largest supplier of athletic shoes

apparel globally blah blah blah their

product lineup includes various Brands

like Nike golf Air Jordan Converse um

and at the at the bottom it says so if

you're looking for some sporty swag

Nike's got you covered so it's friendly

it's got emojis we didn't see really a

joke yet but we will in the future um

but let's look at the log so obviously

it updates the window buffer memory with

what we said and as you can see it has

the past interactions it has capital of

Illinois Florida so it knows what we

talked about previous L and then it

gives the input to the chat model it's

going to come hit Wikipedia so the query

for Wikipedia was literally just Nike

comma Inc so it took that based on what

we originally asked it which was what

does the company Nike do and so it used

the chat model to figure out that it's

going to send the query of Nike Inc to

Wikipedia we got this big response it

pretty much scraped the page of

Wikipedia but then the chat model is

coming back and it is taking that and

then formatting an output that's easier

for us to read because it's more concise

and that's where it threw in the Emojis

and um the sort of joke at the end and

then finally it's just going to update

the window buffer memory so now we see

what we asked and um finally what it

answered to us so let's try um we'll try

to get the calculator to involve so

what what is 12 * um

[Music]

52 we'll be able to look at the log of

what it did so the result of 12 multiped

52 is 624 math can be so much fun can't

it so there's another um the

friendliness coming out of the prompting

that we gave it so once again it updates

the window buffer memory it looks

through it it hits the chat model with

what we asked which is what is 12 * 52

and then it hits the calculator query 12

* 52 response 624 it takes that input

from the calculator and then makes this

output for us and then finally outputs

the um response in the window buffer

memory so it has all this context of

what we've talked about so

far so the logs are very important to be

able to look through and understand

what's going on you can see step by step

which is good for you know once you have

multiple tools and you need to

troubleshoot you know the prompt you

need to redefine it so it's taking

action in the right step or it's hitting

the right tools um sort of as necessary

and now let's see if we were to switches

to a conversational agent let's just see

if it changes anything like that we will

come in here and add a system message

once again which it has this default one

which is huge um assistant is a large

language model trained by open AI

designed to be able to assist with a

wide range of tasks constantly learning

improving so this one's going to

hopefully give us a humanlike message so

I won't even add anything right now

about like emojis or anything like that

we will just chat with it again to see

um any difference so let's do another

one where it will talk to us so can you

um give us some key

highlights from Apple in the past year

let's see what it says here so it should

be looking through Wikipedia and we

didn't even really prompt it in that it

has that tool but it should still be

able to go through it so it did Apple

Inc has been actively announcing new and

redesigned products as well as upgrades

most announcements take place at

high-profile press events that draw

significant media attention um so we can

take a look at the log obviously it

updates hits the chat model to figure

out what to do the output is action

Wikipedia Apple Inc 2023 highlights and

then it search Wikipedia got that big

response and then it formed the response

with um wow that's a huge chunk but then

it gave out the final answer and then

this is what we see right over here so

that's how that one work works with the

log see if there's anything else that we

could take a look at in here um I guess

you can see right here so right here you

know how it says take prompt from

previous node automatically um it's

looking for an input field called chat

input so that's what's right here chat

input but we could also just Define

below and we could drag that in so it's

going to be referencing the same thing

which is we asked can you give us some

key highlights from Apple in the past

year and so this is where you could also

um give some more context as to what

exactly you're looking for based on the

user query that sort of thing um so

let's see now let's just add at the

bottom of this one

to um make sure to

always tell a joke at the end so we'll

see what that one does with the

conversational

agent let's ask about

um what should we ask about something

that it would search Wikipedia for

actually no let's just do another

calculator thing so what

is

2,784

2784 um divided

by

16 see what we get here when it hits the

calculator tool the result of 2784

divided 16 is 174 oh wow is that

actually an even number

um good example I guess but um yeah I

guess this one didn't actually give us a

joke probably because of it has this

huge other prompt

but yeah that's just sort of the

difference between um using these two

and um we saw what happens if you take

away the window buffer memory we saw the

way you could look through logs in order

to see what takes place and you can also

in real time um see it happening so let

me just show that real quick what is um

Nvidia so we hit that and we can see

it's hitting the brain it's up it

updated this and now oh it actually

answered just based on the model it

didn't even go to Wikipedia um but this

is the result we get so it pretty much

gives us key areas where Nvidia excels

um stuff like that and once again you

can look through the log so we can see

that it didn't even hit Wikipedia it

would have gone through here then hit

Wikipedia then came up so let's just do

an example of that actually um can you

provide information about Honda

uh the car company so this one probably

will go to um Wikipedia we'll see it

hits the window bu for memory goes here

and then it knows to search Wikipedia to

get that information and now it's

turning that information from Wikipedia

into a response that we can digest

easier so here's some information about

Honda key highlights stuff like that we

could obviously prompt it to make this

more concise or to use emojis and jokes

and stuff like that but hopefully that

gives you a good understanding of you

know the actual interfacing of agents

and how they they work as far as their

process so the next thing to do from

here is we want to talk about um the

other AI nodes so once you come in here

and you click Advance AI you've got all

this stuff obviously so we've kind of

talked about the agents um we've seen

some stuff with open AI but we'll talk

about it real quick and then we have all

this other stuff and then we have other

AI nodes in here too so this is where

back at the beginning I was talking

about you don't always know when to use

which one and it can be overwhelming so

um we're going to hop back into the

slides real quick and just sort of go

over when you would want to actually use

each of these a nodes all right now

we're going to look at these seven other

AI nodes in nadn open AI is the one that

you'll probably use the most often

that's the one that I use most often

usually just to message a model but

we'll sort of break that down and then

we've got llm chain information

extractor question and answer chain

sentiment analysis summarization chain

and then finally text classifier so

let's hop into um this first one here

which is going to be open AI so what

this one does is it connects to open AI

models like chat gbt um so that's where

you can choose you know 40 4 mini 3.5

turbo whatever you want that's where you

can choose that and you can use this to

generate text um you can talk to a model

like chat gbt you can analyze images you

can create audio or more based on the

sort of the function you choose and the

way that you instruct the node to work

you're going to want to use this one

when you need to interact with a general

purpose AI assistant ask questions

generate texts um create summaries or

even analyze content from images and you

know something like the the

summarization um chain can also

summarize but sometimes you need to have

a multi-step thing within this node

that's going to summarize and then

extract certain things or summarize and

then create new things so that's sort of

why you'd want to use this it's very

powerful so something like creating a

customer support bot that can answer

questions um based on like a summary of

a huge report or something like that and

then we have the basic llm chain so this

one's going to provide a very simple

streamlined way to send a prompt to a

large language model llm and get a

response so you want to use this when

you're doing something very

straightforward where you need an answer

or output from an AI without complex

configurations so if you're asking AI

for a quick response to a user's

question like what are the best

practices for email marketing it would

hit that llm and then answer you right

away so then we have information

extractor this one's going to pull

specific pieces of information from a

block of text that's usually organized

in a structured format so you want to

use this when you need to extract

details from um text such as pulling out

names dates locations um you know from

emails or messages or documents

something like extracting customer

details from a email to pass it into

your CRM

automatically Okay so we've got four

more these two question and answer chain

tensent analysis for the first one Q&A

chain you're going to use this um when

you want AI to answer questions based on

specific documents or you know content

you provide so like a knowledge base

rather than general llm internet

knowledge you want to use it when you

want to limit the ai's answers to

specific documents um and a good example

would be a Q&A assistant for employees

that are um getting questions answered

based on the company's policy documents

or specific training

material then we have sentiment analysis

this one can analyze a motion or tone of

a piece of text and it can categorize it

as like positive negative or neutral so

you want to use this to understand the

mood or attitude behind um like a

customer feedback or certain social

media posts or reviews about your

product or something like that um you

know it's going to automatically analyze

those emails and then sort of give you

the tone that was it was written in sort

of

thing so then we have summarization

chain um what this one does is it's

going to condense long pieces of text

into shorter summaries and it's going to

capture those main points and highlights

for you um you can use this to create

summaries of lengthy documents obviously

making them easier to read or pass

through um quickly and then you can you

know summarize meeting transcripts or

feedback documents or policy documents

in order to make sure that you're

getting all the the key information from

it and then finally we have the text

classifier which categorizes pieces of

text or a piece of text into predefined

categories based on the content of what

it's reading it's going to automatically

label or classify texts such as sorting

email into different departments or

tagging um different types of customers

or tagging different types of feedback

um an example would be you know

classifying incoming support tickets

into categories you could have like

billing tickets technical issues

customer support General General inquiry

and then you can route them based on

this classifier into different logic of

you know where it could get sent around

so all these nodes obviously very

powerful um it's important to understand

when is the best use case for each one

but they're all just ways that you can

add um large language models you know

artificial intelligence into your

workflows in order to make them even

more powerful than you know static

automations all right we're sort of

starting to wrap up the master class we

just talked about these other Advanced

AI nodes right here besides the agent

we've got these ones that we just talked

about in those slides and finally just

wanted to end off by talking about these

other AI nodes in here because once

again it's a little overwhelming so

first off I want to say that um in my n

andn Master Class video If you guys

haven't seen that I talk more in depth

about the document loaders as well as um

the text Splitters that are down here

and then also sort of vector stores so

for more in depth I would go watch those

videos because we sort of get a workflow

where we talk about what's going on in

each of these sort of AI um steps but

first one we have document loader it's

just going to bring documents into the

workflow for processing like um loading

PDFs or text files and like I said if

you need more information um this is

pretty much how it looks and then you

add the text splitter which are you know

down here and I talk about these more in

depth in the nadn master class video

then we have language models so as you

can see these are the different models

that you can choose from um I pretty

much use open AI the most of the time

but these are just models I can

understand generate language and they're

used for tasks like answering questions

or creating text when you want to talk

to something like you know GPT or

claw and then we have memory we've

talked about this again um you've got

the option for window buffery which we

have right here or sorry window buffer

memory we have right here and then these

other options basically just storing

information temporarily during a

workflow so the AI can remember um these

details to reference later then we have

output parsers we talked about these

earlier too um we have retrievers which

search and pull relevant information

from a specified Source um and this is

just so that they can sort of assist in

answering questions and finding details

so we've got different options here um

Vector store seems to be the one that

I've used the most but you've got

different options as um of course

because there's just so many to choose

from and then after retrievers we have

text Splitters we talked about those um

tools this is where you can either call

n andn workflow or there's a ton of

Integrations as you can see um and these

are just going to give you um you know

actions Within These popular systems

that you probably use every

day then we have our embeddings this is

just going to convert text into a vector

um format which helps tasks like um you

know Rag and semantic search finding

similar content so if you don't

understand these embeddings I would also

maybe go watch that NN masterclass video

we talk about you know pushing data into

a pine cone Vector database and it's

going to push it into a document loader

to load the data split it up embed it

into the um Vector database uh in the

vector stores down here which you can

see Vector stores are going to store and

retrieve um these Vector sort of

numerical multi-dimensional repres

representations of data or text and

making it really easy to def find for

the agent based on you know related

content sort of based on the meaning of

what's going on so these are the vector

store options and then finally we've got

miscellaneous which I don't even really

knows in here it's open Ai and then chat

memory manager so within the window

buffer memory you have the option to get

messages insert messages delete messages

so that is sort of what's going on here

um a lot of the times you won't be

really coming in here to grab these

nodes they'll be you know you'll be

grabbing them from something else like

you know when you need to text split or

when you need to sort of load data stuff

like that so I hope hopefully that at

least gave you some general context on

this and this because when you click

into AI noes obviously um there's a ton

that's going on in here so yeah I hope

that that made sense so that is going to

be it for this master class where we

talked about a lot of the aspects of AI

agents specifically within NN so let's

just quickly go over what we covered we

started with the basics of AI agents we

explored how these agents can automate

tasks we talked about their triggers we

learned about setting up the workflow we

took a deep dive into each of the agents

because when you open up an agent you've

got a tools conversational plan and

execute um and more and each have sort

of unique strengths and use cases so we

talked about what they each do and when

you would want to use each one then we

talked about JavaScript functions and

variables which are super important when

you want to build agents or even just

build workflows in Ann um they help make

our workflows more Dynamic and

customizable then we talked about some

key settings within the agents like

prompts and system messages and you know

the other options and settings and how

we want the agents to interact we talked

about some output parsers to ensure that

responses are structured in the way that

we need them and then finally we just

dove into some of the other AI nodes

that are available within naden to

extend the power of your workflows stuff

like document loaders and beddings and

um you know text classifiers sens

analysis that sort of stuff so at this

point um if you're excited about

building AI agents within nnn there's so

much more to explore feel free to check

out other videos on my channel where I

dive into you know building Advanced Air

agent and different simple workflows and

end in end step byep or even live builds

um you know some more real life examples

and more in-depth looks at each of the

tools so um finally I just wanted to say

um feel free to join the school

Community there's you know it's growing

really fast and a lot of people are in

there you know talking about n Talk NAD

talking about other ways to you know

improve workflows or getting help on

certain workflows and I would love to

just you know see all you guys in there

cuz it's really nice to interact and you

know see what people are working on see

what people want to see from future

videos um but that's really all I've got

for today um if you made it this far

really appreciate you guys taking the

time out of your day to watch this video

and I would really love some feedback

cuz I hope these sort of longer form

ones are um educational and at least you

get a few things learned out of the

videos but again I really appreciate all

the support lately and um thank you so

much for watching I'll see you guys in

the next video
all right we are back with another

master class this one is about prompting

and prompting specifically for AI agents

this course is designed to take you from

a complete beginner to almost an expert

in creating effective prompts

specifically for AI agents by the end of

this you'll be able to design prompts to

make your agents handle complex tasks

autonomously confidently and reliably

wanted to start off with showing a quick

agenda of what we're going to be going

over in the master class today that way

you can see what you're in for and see

how each module is sort of going to

build on the last one but if you're not

a complete beginner feel free to skip

around if you want to go towards the end

because we're going to start off with

the basics and sort of build our way up

from there but anyways five total

modules today with a bonus module at the

end the end is just going to talk about

some emerging Trends and some of my

thoughts about the prompt Engineering in

the AI space and anyways module one is

sort of an introduction to prompt

engineering for AI agents module two we

get into Core Concepts of prompt

engineering three essential prompting

techniques four mastering structured

prompt Frameworks and then five Advanced

tools and techniques for prompt

optimization real quick just wanted to

mention if you guys like this type of

content please feel free to join my free

school Community the link is down in the

description um we have a great community

of people that like to talk about NN

primarily but just all things sort of AI

automation related I also post all of

the resources I use in my YouTube videos

on this school Community for free so

workflows and end and end and stuff like

that then if you want to take your a

automation skills one step further I've

got a paid community that you can join

as well great Community great network of

people in this space we have multiple

live weekly calls as well well as uh

monthly competition with real prizes

we've got a classroom of different

modules that are going to be

continuously updated every week and

expanded as the space rapidly changes so

I'd love to see you guys in either of

these communities get the chance to meet

you and definitely just reach out okay

so welcome to module one which is

Introduction to prompt engineering for

AI agents in this module we'll introduce

you to the concept of prompt engineering

and explore why it's critical for

working with AI agents so let's just

Dive Right In here so what is prompt

engineering simply put prompt

engineering is the process of creating

inst instructions called prompts that

guide an agent to perform a task exactly

the way that you want it to so sort of

like programming but instead of using

Code you're using natural language so

almost as if you're talking to someone

you're basically just telling the AI

what to do in plain simple terms but

prompt engineering is more than just

writing instructions it's about thinking

carefully how you phrase things to get

the right output every time so think of

it like you're giving directions to

someone who can only listen to you one

time there's no back and forth

conversation you're not able to clarify

things you need to be precise from the

very beginning so here's a simple

example let's say you're using an AI to

help with scheduling a clear prompt

might be something like create a meeting

for Thursday at 3 p.m. with John and

include a video link that prompt you

know it's very specific it's very

actionable and it leaves almost no room

for

misunderstanding so why is prompt

engineering important this is because it

makes your agent more reliable so when

when your prompts are clear well

structured the agent is going to perform

tasks accurately and consistently and

this is obviously important for things

like um things that are going to happen

repeatedly or things that involve a lot

of data like customer support data

processing or scheduling so in this

master class you'll learn how to design

prompts that are precise efficient and

optimized specifically for AI agents you

know mastering prompt engineering will

allow you to create prompts that make

your agents handle more complex

workflows on their own which which is

sort of you know the whole goal of AI

agents so now let's talk about why

prompting AI agents is different and

also important than just prompting you

know a large language model or chat

gbt so when you're talking to chat gbt

it can be very conversational it's like

you're asking them to answer questions

and you can sort of follow up so you can

go back and forth like I said you can

follow up you can clarify you can fix

errors as you go but with an AI agent

you pretty much put that prompt in there

when you're building out your your

workflow and that's it they have to

understand and execute what you want

your instructions in just one single

try so imagine the scenario you're

running a business and an AI agent is

set up to manage hundreds of customer

inqueries every day it has to answer

each question or request correctly

timely without needing extra

clarification and you also don't have

the time to go check and make sure that

every single response is correct the

agent just has to work and you have to

trust that it's going to work so that's

why prompt engineering for agents is so

important because it's all about getting

it right that first time so this becomes

even more critical when you're using an

agent for you know tasks like data entry

or lead qualification that kind of stuff

they need to be accurate they need to be

reliable and if they're vague or unclear

the agent is going to produce

inconsistent results which could lead in

errors which could lead to errors in

customer interactions or within your

internal business processes which is

obviously what we're trying to avoid so

you know basically it's all about

precision and Clarity and by the end of

this course you'll be able to know

exactly how to design these prompts to

empower your agents to do their jobs

autonomously okay already on to module 2

which is Core Concepts of prompt

engineering so in this module we're

going to dive into the essential

building blocks of every good prompt

we're going to understand that these

core components will give you the tools

that you need to craft effective prompts

for any task let's talk about the key

components of a prompt so each component

plays an important role in telling your

agent what to do think of these

components as sort of like a checklist

to make sure that your prompts are clear

structured and you know set up you and

your agent for Success the first

component is background so you want to

give your agent background information

so it has a basic understanding of the

task or context that it's working in

this can include details about the

subject the company or the specific

context that might influence how the

agent is going to respond so here's an

example if the agent is helping with

customer support you might include you

are a customer support assistant for a

tech company that values quick and

empathetic service so obviously it's a

very simple example but that's sort of

the kind of stuff we'd be looking at

here next is context this is all about

narrowing down the focus for the agent

so you want to give it specific

information on how it needs to handle

the tasks accurately so if your agent is

scheduling a meeting you might add the

calendar should prioritize meetings with

department heads and limit meeting times

to no more than an hour this way the

agent has a much better understanding of

the conditions to actually work within

and how to go about its

tasks then we have instructions so this

is kind of the heart of the prompt this

is where you tell the agent exactly what

to do instructions here need to be you

know obviously clear and specific so for

example you want to write you want an

agent to write a product description you

could say write a 100w description for a

smartwatch highlighting its Battery Life

Fitness tracking and water resistance so

as you can see here not much room for

misinterpretation there it's very clear

very

specific then we have tools so obviously

when you're working with an AI agent

you're going to give them different

tools so that they can actually take

action on your behalf and you need to be

able to define the tools and when to use

each tool so that it knows what to do

and that it's not um you know calling an

email tool when it really should be

getting information from a database so

the agent's going to have multiple tools

usually so that's why you need to Define

it very clearly so obviously you would

like list out here are the tools you

have access to and then you put calendar

tool and a bunch of other tools and then

for each tool you wanted to find it like

use this to find free time slots for

scheduling meetings this is also

interesting because in a multi-step

workflow you could say like let's say

you have a tool to get contact data you

have a tool to um make an appointment

and then you have a tool to send an

email you could bake in the steps when

you're defining each tool for example

with a contact database or with emails

in one of those steps you can say like

you must call the contact database tool

first so that you know the email address

to send in the email tool so you can

sort of make like a flow by defining how

the tools work in conjunction with each

other and then finally in this section

what we're talking about as far as

components um we have examples examples

are incredibly valuable they show the

agent what kind of response that you

expecting so this is going to help the

agent understand tone format um details

flow so for example if the agent needs

to get contact information from a vector

database then use that email to reach

out and then schedule a calender event

you would want to give an example of the

query the agent would get and then the

actions that the agent needs to take so

like I said just giving an example of

what it should expect and then what you

should expect type of thing but anyways

each of these components these five

components are going to help the agent

understand exactly what you're looking

for using these in your prompts makes it

more likely that your AI agent agent is

going to deliver the results you want

every time but there's also a fine line

because you don't want to just pack it

full of information and we'll get into

you know how you make your your prompts

effective without just info dumping

basically so yeah next we're going to

talk about tokens understanding tokens

and cost efficiency when it comes to

tokens um so a token is a term that's

Central to understanding how prompts

work and how a i processes them in the

simplest terms possible a token is just

a piece of language a unit of data that

the AI is going to read and understand

um what you're asking for so think of a

token like a chunk of text so in this

example AI is amazing each part of this

sentence may be its own token even

punctuation so this could have four

tokens right here AI is one of them is

is one of them amazing is one of them

and then the exclamation mark would be

the fourth token there so you have

different options of how you want to

split up your tokens that sort of thing

but just in general think of it as the

way your text is being split up and um

it doesn't have to just be text but the

way something's being split up and put

into um a way that the AI can understand

what you're asking for why do tokens

matter so the more tokens you use in a

prompt the more computational power and

cost that it's going to take for the

agent to process so this is especially

important if you're using AI for tasks

that happen frequently or involve a lot

of data because those tokens will start

to add up you know they directly impact

how much your agent interaction will

cost cost if you're using an API that

charges by the token like open AIS so if

you have a 500 token prompt it's going

to cost more obviously than like a 200

token prompt so that's why learning to

write very lean but still very efficient

and clear prompts is a very important

skill which obviously this is kind of

why I wanted to make this course and so

why do tokens matter obviously it's

about saving money but efficiency isn't

just about saving money it's also about

getting the AI to respond faster and in

a more streamlined way so for instance

if you have a prompt that's way too long

and complex it's going to slow down the

response times which you know how long

your agent takes to respond and get the

job done but also it's going to increase

the likelihood of error within your

workflow so whenever you're crafting a

prompt think about the tokens you're

using and um you know think about if

they're all necessary could you make

your prompt more concise without losing

you know the context and the clarity

without losing the information you

already have in the prompt this is where

the skill of promp compression comes

into play we'll cover this more in depth

in module 5 but you know prompt

compression really going to come in

handy here when you're going over your

prompts but just wanted you guys to

understand tokens and the aim for cost

efficiency which is going to help you

make smarter choices when you're

creating your prompts as far as keeping

them clear and um budget friendly at the

end of the day now that we have an

understanding of the main components of

prompt and we understand tokens let's

introduce a concept that's at the core

of prompt engineering for AI agents

which is structured prompting and this

is just basically a way of organizing

your prompt in a clear logical format

unlike a casual conversation where you

can sort of be vague or backtrack a

little bit structured prompting make

sure the agent has all the information

it needs upfront in a specific order so

why does this structure matter it's

because it guides the AI through the

prompts like a set of instructions it's

going to tell the agent what's most

important what to pay attention to and

how to proceed step by step structured

prompting is especially valuable for AI

agents because a lot of times they need

to handle complex tasks autonomously so

imagine you're giving instructions to

someone who can only listen once without

the chance to answer questions this is

going to help you be precise so that the

agent doesn't misunderstand or Overlook

important details you know each part of

the prompt has a purpose and a place

sort of like a recipe with um specific

steps to follow in the correct order

let's break this down with a quick

example so suppose you're designing a

prompt to get an AI to draft an email a

structured prompt could look like this

so we've got the roll object or sorry

role objective context instructions and

example the role is that you're a

professional assistant writing an email

on behalf of an executive the objective

is the goal of the email is to thank a

partner company for their recent

collaboration context the partner

company helped with a recent event that

was a success and we want to emphasize

our appreciation and hopes for future

projects So the instructions are to

start with a greeting mention the

success of the event thank them for

their contributions and close with a

line about looking forward to Future

collaborations and then as far as an

example we want to outline sort of the

input that the agent's going to get and

then the way that it should respond so

the user here would say draft an email

to thank ABC Corp for their partnership

on the recent marketing event the AI

agent would then respond with um dear

ABC Corp I wanted to extend a heartfelt

thank you on behalf of our entire team

for your invaluable support in making

the recent marketing event of success

your expertise and dedication truly made

a difference and we appreciate all the

hard work blah blah blah signs it off as

email so as you can see because it had

all of you know the background

information about its role and its

objective and its context um it knew

sort of how to structure that email and

then this is going to give us consistent

time consistent results every time we

ask this agent to sort of make an email

for us obviously each part um guides the

AI in a very logical flow and it's going

to proove the accuracy consistency and

all that good stuff before we finish

module two there's an important concept

I wanted to talk about real quick that

you may have heard about

in regards to AI agents which is AI

hallucination AI Hallucination is the

term used when an AI generates a

response that seems plausible but it's

actually like completely made up or

incorrect and this happens when the

agent fills in gaps in knowledge with

information that it just invented it

sort of hallucinated and gave you that

response it's going to be common in very

complex or ambiguous prompts where the

agent might not have clear guidance on

what to do next what to say and so this

happens when the agent doesn't know

information in the way that we do so

instead they predict the most likely

next word sort of based on their

training data or based on the model and

sometimes they will overreach and they

try to provide information that they

weren't trained on yet or that they

don't you know know so this leads to

them making up details so for example if

you ask an agent about a specific but

fun but fictional event it's going to

create details around that event to give

you a coherent answer even if these

details aren't accurate so like on the

one hand it's super cool that we're at

this point in technology where we have

generative AI that can be creative and

that can make things up and help you

with ideas but at the end of the day we

need to make sure that we're structuring

our prompts efficiently and effectively

so that they don't you know go to this

space where they hallucinate and make up

information especially in you know a use

case where like let's say you were in

you know the healthcare world and you

needed help with the medicine and they

just start making up answers that is Bad

News Bears then the question is how do

we actually reduce AI hallucination

using our prompts so I I don't know if

it can be like completely eliminated you

can definitely reduce it to a bare

minimum and mitigate that risk by having

clear concise prompts so here are my

tips for doing so obviously you want to

be specific the more precise that you

are the less likely it is that the agent

will stray away from the facts that it

has so avoid ambiguous questions or

leaving too much room for interpretation

so like instead of saying um explain the

causes of recent business Trend you

would say like list three specific

factors that contributed to the increase

in um online shopping during Co 2020s so

that sort of thing very specific and now

it's going to it knows what to zero in

on rather than just you know making up

things next we have providing context

and constraints so include background

information that guides the agent and

sort of sets limits on the type of

information it should give so you know

tell me about climate Solutions is going

to leave it up very vaguely that's why

again with same same thing the last

example you want to say like list only

three solutions that were backed by

science for climate you know that sort

of thing I'm no scientist um anyways

request known information only so if

it's possible ask the agent to only

provide responses based on widely

accepted knowledge rather than

hypothetical um scenarios and then

finally check for consistency so when

you're working with the agent for

complex tasks it is good practice to

verify the output especially if the

agent is used in situations where

accuracy is crucial like customer

support or decision- making or um like

medicine like I previously talked about

that sort of stuff but those four tips

are you know they'll definitely put you

down the right path as far as you know

making sure your agent is not

hallucinating and making up stuff quick

recap of module 2 we talked about prompt

components we talked about tokens and

understanding the cost efficiency and

then we talked about structured

prompting and AI hallucination so now

that you've got these Concepts under

your belt have a solid foundation to

start creating effective prompts so

we're going to go into that next module

where we talk about essential techniques

so let's just move on to module three

okay module three is essential prompting

techniques in this one we're going to

dive into the essential prompting

techniques to make your prompts more

precise and effective for AI agents role

prompting we have briefly talked about

it in that previous section with

structured prompting we talked about

outlining the role at first but

basically role prompting is just

defining a specific role or you might

hear persona for the agent to adopt in

order to align its responses with a

specific tone specific expertise and a

specific um focus so for example you

wanted the agent to handle customer

service queries you would assign it the

role of a customer service

representative and that helps the agent

you know be friendly and professional in

the way that uh customer service rep

would be so here's why role prompting

matters when you define the role it's

going to understand you know the

language and the level of expertise and

the approach that it should use so yeah

pretty self-explanatory let's let's get

into it quick example suppose you want

the AI to explain a complex product

feature you could prompt it like saying

you are a technical expert explaining

explaining this feature to a customer

with basic knowledge you simp simple

language but provide detailed insights

into how the feature works so this is

going to be super helpful as we move

into more advanced tasks where you need

to make sure that you and your agent are

both aligned on the type of tone and

focus that it's going to be taking on

then you might have heard of few shot

prompting so this is a technique where

you provide the agent with a few

examples of inputs and outputs this

helps guide the agent's response style

format flow and even sort of helps them

categorize decisions so I'll show an

example of categorization in a sec but

by showing the the agent examples you

sort of set the standard for its

responses and it's going to make them a

lot more reliable and

consistent so here's an example where

let's say you're using an agent to

classify customer feedback and it can be

positive neutral or negative and then

you can prompt it by showing these

examples of what a positive feedback

looks like what a negative feedback

looks like and what a neutral feedback

looks like um which is going to you know

just help the consistency of the agent's

responses coming back then we have Chain

of Thought in which is especially useful

for tasks that involve multiple steps or

sort of logical reasoning to go through

to take place with this type of

technique you can ask the agent to Think

Through tasks step by step and that's

going to help it process information in

a logical order and it's going to

improve the accuracy of sort of the

final result so like I said IDE deal for

complex tasks you know with like

calculations or comparisons or you know

multi-steps within a step so this is

when you'd want the AI to make sure it's

following a sequence of instructions

let's say you want the agent to

calculate total cost of an order with a

bulk discount and a shipping fee if you

just told it that I don't know if I I

don't think it would do it correctly um

so anyways the prompt you could say you

calculate the total of total cost of 100

units price at $10 each you would apply

a 20% discount and um for anything over

50 orders you would add a $25 shipping

fee so your Chain of Thought prompting

you can show the actual steps

multiplying the units by the price and

applying the discount and then the

shipping fee and then you get to your

final answer so this obviously just

shows an example for the AI agent of

breaking down the tasks making fewer

errors and probably producing a more

reliable answer and just super crucial

when you're working with um multi-step

tasks but it's always you know a lot of

times you don't have to just know

exactly what to do when to do it and

later we'll talk about sort of the way

that you can provide feedback and you

can like test but a lot of times it's

just like playing around seeing seeing

if it did it correctly or incorrectly

seeing why adding something in running

it again taking things out running it

again so you it's definitely something

that you just sort of get the hang of

but these are good Concepts to know um

at a high level and then I think just to

close off this module we'll talk about

markdown formatting real quick um if you

don't know what it is it's just

basically the way you can add structure

and organization to text it's not even

specific for prompting or AI agents I

think it's just a thing but um it makes

it easier for both humans and agents to

read things and understand importance in

certain things so you can use headers

bold text bullet points stuff like that

so I'll just fly through this section

because it's not too

complicated but um you know the first

one we'd have headings so obviously

allows you to organize information into

settings it helps the AI recognize that

things are separate which is helpful for

multi-steps or topics and you would do

this by using um the pound sign so this

symbol the hashtag the pound whatever

you want to call it this is you know

like you can do one for a top level

heading two for second level and three

for third level heading and just kind of

break stuff down then we've got bold

text obviously we all know what bold is

and we all know how we want to use this

to highlight importance in markdown you

would do um double asterisk you could

also just do one asterisk but double is

going to be like more important so as

you can see these examples let's say we

wanted to say please make sure to double

check all data points that's super

important you have to double check just

throw that in

bold and we got bullet points um this is

pretty self-explanatory too but you use

a dash or you could use asteris too um

just at the beginning obviously but you

could I pretty much always just use

dashes and then the agent knows it's

like okay these things sort of all

relate because they're all like a list

or instructions that sort of thing then

we've got horizontal lines which are

good just to separate actions to create

a very visual break in a prompt or in

you know some sort of information so

when you're when a prompt gets pretty

long and you just want to break things

up throw in a line it's just a simple as

throwing in a line then here's just a

quick example just to show it all sort

of piece it all together we've got a

header up top and a header at the bottom

so that we know these are like sections

we've got a numbered list 1 through four

and each of those numbered

lists um are bolded like the actual

information and then within each of

those sort of numbered lists we've got

bullet points within those two so that

lets me easily see like what I'm looking

at and also the agent is able to

interpret that too I didn't throw in

horizontal lines here but let's say at

the bottom after the conclusion you

could throw in a horizontal line and

then below that line you could have just

like extra notes in case you wanted to

just highlight a few extra things but

that's sort of you know how it looks

just to finish off this module real

quick we've got a section about

emotional manipulation and importance so

kind of similar to the idea of markdown

with like making things bold and making

things look more important but this

technique involves using language that

adds a sense of urgency or importance or

even emotional weight in some cases so

it sounds dramatic but adding urgency

can really help ensure that the agent

prioritizes certain parts of a task so

you know by using strong language the

agent will understand what's

non-negotiable and what is like

particularly more important than the

rest of the prompt quick example let's

say you're using an agent to send a

reminder email for an urgent deadline

you could prompt it like saying draft an

email reminder to the client about their

upcoming deadline it is absolutely

essential that the client understands

the urgency of submitting their

materials by the deadline missing this

deadline will ruin the project timeline

so words like essential urgency ruin

ruin in all caps um you could even make

some of those words bold if you want but

it adds you know an emotional weight to

the task and single signals the agent

that the message needs to convey some

sort of urgency and it can be very

effective when you're when you need to

prioritize certain details or you have

you know deadlines or safety hazards or

you know anything critical you can

definitely use some emotional

manipulation there quick recap of module

3 we covered role prompting few shot

prompting Chain of Thought prompting

markdown and emotional manipulation and

importance all of these techniques you

can sort of bake into your prompts which

are going to make them more reliable and

sort of help you align your agent with

your goals so now we're going to get

into module 4 which we're going to talk

about some structured Frameworks for

organizing prompts that are really going

to help you take them to the next level

all right module 4 we have mastering

structured prompt Frameworks in this

module we're going to explore structured

Frameworks to help you organize your

prompts effectively using these

Frameworks can help you make your

prompts once again the common theme

making them more accurate and reliable

so let's get into this module so when

you're prompting an agent there's

usually two sort of structured

Frameworks you want to use it's either

long structured or short structured or

at the end we'll talk about a more agent

specific one but either way long

structured you have the key components

of roll objective context instructions

examples and notes when you combine

these elements the agent is going to

have all the information it needs to

generate a comprehensive accurate

response these long structured ones are

usually better for tasks where there's

multiple steps obviously and things are

critical like generating a report or

analyzing data or providing some sort of

detailed summary and it has to grab

information from somewhere else and then

the short structured is kind of just

like a streamlined version of the long

structured prompt because sometimes you

don't want to overwhelm your agent

that'll actually just confuse it and

once again you know like a lot of times

I'll start off with sort of a long

structured and then test it a few times

and then take things out and see if it's

still working and it obviously is more

efficient and then it's going to be

cheaper with your tokens but it doesn't

need much context or detail in this

version it's going to be more

straightforward tasks like quick

responses or summaries or even

classifications where the AI doesn't

really need a ton of background

information it's just something that it

could do right away because it's a task

if that makes sense but here you're just

going to give it an objective what it

needs to do how it does it and then if

you even need to you can give an example

so a lot of times I'll use like a long

structured one in like an agent that has

multiple tools to call or multiple

workflows to call and then a short

structure you could use use for

something like a message and model node

or even like one of those sub agents in

a larger agent workflow where it only

has access to just email actions or

something like that so you kind of got

to play around with it but it's

important to understand the two

different

Frameworks or of course the third

framework we have a more agent specific

one and I think that this one I like to

think is more when you've got an agent

with multiple tools or multiple agents

that it has access to but anyways this

is tailored towards the a agents because

they need to make decisions inter act

with more tools um handle tests that are

a higher degree of autonomy basically so

in this framework we incorporate some

extra components that help the agent

understand sort of its its standard

operating procedures and all the

available tools so we're telling it its

role objective it's sop tools and sub

agents so that's sort of why this one's

more specific for agents and then

obviously instructions with examples at

the end so by including you know like an

sop and Tool descriptions it's going to

give this agent more guid

and give it the information it needs to

act autonomously which is kind of the

goal of AI agents obviously so it's

ideal for you know self-guided agents

that want to operate within a specific

set of guidelines and responsibilities

and when you do this right it can be

super super effective as far as the

agent being able to just completely be

like a virtual assistant basically so

module 4 was really quick just want to

recap we did long structured short

structured agent specific and like I

said you kind of want to play around but

these are good Frameworks to help you

approach crafting your prompts and

testing them and um you know making

changes as necessary but let's move on

to module 5 this module is all about

Advanced tools and techniques for prompt

optimization we're going to explore some

other tools you can look at not go too

in depth but just kind of open your eyes

as to how you can get more advanced and

you know like refine manage test and

give feedback to the AI so let's get

into this module so just a high level

overview of two tools we'll talk about

which is prompts layer and using cost

calculators and I'm not going to dive

too deep into these tools but obviously

just wanted to give you a sense of how

you could optimize but prompts layer is

a tool that's going to help you track

test and manage multiple versions of a

prompt so that's how it really comes

into play where you can you know store

this one and test out this one and

document responses and all this kind of

stuff but yeah like I said it's going to

allow you to sort of run a a andb tests

compare different versions see what

works best you can track your history

you can measure changes for accuracy and

performance so this is going to help you

choose the most effective prompt for

your specific task and um it's it's cool

you can kind of store these and look

back at them and then later when you

have a similar use case or a complete

different use case you know sort of what

to do what not to do and then we've got

cost calculators which I think are super

cool especially you know earlier we

talked about tokens and cost and

efficiency but when you're working with

large language models you know obviously

we have our tokens and they impact the

cost so you can use a cost calculator

like this one I think I just typed in

open aai cost calculator pops up or no

open Ai tokenizer and then you can put

in prompt so in this example we have

super simple prompt about acting as

customer support for small online

clothing store and it shows us that it

was 35 tokens 223 characters and you can

choose a different model that you're

going to be running it through but

they'll tell you exactly how much you

know you how many tokens so that you can

kind of control the cost and adjust your

prompts to reduce your token count which

is pretty cool so this kind of stuff

like I said it's going to allow you to

streamline the process of your testing

and your cost estimation which is going

to be super big when you start running

agents at scale and you just you know

running them over and over multiple

times a day jumping off of that wanted

to talk about prompt compression and how

you actually make them smaller and save

money um you know this is obviously all

about reducing unnecessary tokens

without sacrificing the quality which is

the most important part because you

still need the actual content of your

prompt to get through to the agent so

after this module if you want to know

more about the technical details behind

prompt compression and how you actually

get in there and really do it um go

check out Mark cf's Channel I I just

watched a video from him about um promp

compression and that's where you know

these next slides two methods that he

talks about is that's what I'm going to

talk about but he goes way more in depth

and great video so go check that out but

anyways he talks about two methods to

actually compress your prompts the lazy

method and the technical method and I

completely understand why it's called

that because I definitely use the lazy

method but this one just involves

manually removing redundant or

unnecessary words from a prompt using

like chat gbt or using AI to make your

AI type of thing so you know there's

also custom prompt compressing gpts but

basically you just want to tell it that

the goal is to keep the core elements

and communicate the same information but

just get rid of the unnecessary wording

so in this example we have an original

prompt um which is I would like you to

please generate a detailed summary of

this report focusing especially on the

areas that are most important but you

could also just compress this down to

summarize the key areas of this report

and pretty much gets the same message

across so obviously it's just like the

same concept of like when you're writing

an email or when you're writing a draft

or a report like you just want your

wording to be concise so same concept

here and then the technical method uses

um you know algorithms or different

Tools in order to identify which

specific tokens are high value and then

which ones can just be taken out and

this method is really interesting

because these tools analyze the prompts

and identify specific words that don't

actually impact the response so it'll

take them out and it's obviously very

useful when you're working with long

prompts and sort of a high volume um

environment as far as your workflow

because it's going to maintain the

consistency but keep your cost down

and it's interesting because the outputs

don't always make sense to us because

it'll take out some you know filler

words that are you know important for

gramar and for like flow of conversation

in our head but the AI can still

understand what's going on because it

has those high value tokens in there and

they're you know placed in a specific

order so just to recap efficient promp

compression will significantly reduce

your cost over time and um you can do

that in a couple methods and if you want

to check out technical method definitely

go check out Mark's Channel now let's

talk about iterative refinement and

feedback loops so in prompt engineering

it's rare to create the perfect prompt

on the first try that would be pretty

impressive but you often have to test

refine and adjust your prompts based on

the performance and based on the output

you're getting from your agent so this

process is known as iterative refinement

and so there's sort of three ways to use

iterative refinement first one is

testing and adjusting you'll run your

initial prompt you'll assess the agent's

output if it doesn't meet your

expectations which it probably won't

always exactly the first time then

you'll identify what parts of the prompt

might be confusing or unnecessary or too

loaded or not loaded enough and then

obviously you'll adjust your prompt add

Specific Instructions or remove specific

details and then you'll try again and

adjust and also you can document your

changes so when you make the changes you

document The Prompt and then you note

what you did and then you can note like

how it came out and that way you can

compare different versions and see what

worked best so something like prompt

layer obviously makes that really easy

for you to do storing your versions and

allowing you to track what changes led

to Improvement and then you have example

based learning which is providing

specific examples within your prompt to

guide your agent so we talked about this

a little bit but these examples are

going to help reinforce the desired

output so easier to understand the

context and requirements for your agent

super quick example of iterative

refinement initial prompt Is Write a

brief summary of the feedback report

covering all areas where customers

mentioned concerns and then you would

adjust it to summarize the feedback

report focusing on the top three

customer concerns as you can see in this

example the initial prompt was vague so

we refined it by saying top three

customer concerns to make it more

focused and then through iterative

refinement we also had guided the AI to

produce responses that better match our

expectations finally let's explore

creating and managing feedback loops a

feedback loop is a way to continuously

improve the agent's accuracy over time

especially in a high volume environment

so you want to provide feedback based on

past resp responses that will help your

agent learn from previous interactions

which will make the future responses

more reliable trustable so there's three

things again here we have first

providing clear feedback when the agent

produces an output that's of Target you

want to correct it in a um very you know

in a helpful way directly in the prompt

or through your instructions so for

example if the agent consistently

includes unnecessary details add a note

that says Focus only on the main points

avoid extra details so one example of

doing something like this is if you've

watched some of those email videos i'

done maybe in end end a lot of times the

agent would sign off with um like square

brackets your name your company name and

we would just directly go in there and

say like never never include square

brackets with a variable like always

fill it in with Nate herkelman or

something like that then you want to

establish a standard operating procedure

so if you're using an agent for

repetitive task tasks establish an sop

um for feedback so this could involve

steps like documenting common errors

noting

improvements um setting reminders that

sort of stuff and then obviously you

want to use itative testing we just

talked about that but run different

versions see how they adapt and then

rinse and repeat so to recap this module

covered you know Advanced tools for

testing and optimization we talked about

cost savings as far as prompt

compression talked about iterative

refinement and feedback loops and then

also creating and managing those

feedback loops um within your your

environment all right and now bonus

module just some stuff I thought that

would also be important to include but I

didn't really know exactly where to put

it but the space is obviously changing

so fast so you have to understand that

like prompting may also change and have

to adjust a little bit and like when you

have an agent workflow is running

consistently in a month it may stop

running consistently and you need to go

in and fix the prompting but anyways

we've covered you know Core Concepts

core Frameworks um and techniques but AI

is going to continue to advance and new

trends are going to emerge so I just

thought we'd briefly talk about you know

like these Trends and what's give a

sense of what's on the horizon okay so

advancements in AI models one of the

biggest drivers of change in prompt

engineering is the rapid advancement of

AI models like I just mentioned like gbt

turbo 01 and then the anticipated 5 but

each new generation of models comes with

many different things it comes with

refine capabilities um you know could

have greater accuracy greater

understanding greater efficiency but you

never know sort of how that's going to

affect your current prompts these

advancements mean that these future

models could require less handholding

they could be better understanding

context with fewer examples and they

could be more Adept at following your

structured instructions or they actually

may need more prompting in certain areas

and you know Less in some as well but as

these models grow more

complex they will also probably become

better at picking up subtle nuances that

may require more advanced prompts like I

said to fully utilize their capabilities

so some prompts may include more refined

role assignments or Specific

Instructions to help a model act more

like an expert within you know a

specific field then also tools within AI

agents so this is you know something

that we're doing right now but I could

just see it this space changing a little

bit in the sense of the way tools work

but that's one of the most exciting

things right now is Agents can have

tools and take action on many different

things so because they're being

continuously integrated with different

tools that allow them to access

different things calendar email

calculations databases whatever it may

be this is going to shift prompt

engineering strategies because you have

to make sure you're always outlining

these tools and how they're going to

work so this may require a new approach

to prompts like specific instructions on

how to handle them and I know we talked

about this but just something that um I

wanted to bring up because as tools get

more complex and you know we're already

getting to the place where you have

agents that manage multiple agents and

then those agents manage more agents so

just something to sort of keep in the

back of your mind as far as

prompting them and then finally the last

thing I had was just a specialization

and advanced customization so you know

models are becoming more specialized and

we're seeing that Trend towards

customizable agents so they can perform

tasks within specific domains you know

Finance Healthcare customer support and

they're going to start to be able to

understand probably like industry

specific jargon and like Advanced

metrics of you know like if they're in

finance they'll have Advanced Financial

metrics and finance specific jargon

stuff like that um so this trend is

going to allow prompt Engineers to

customize these prompts further and

really integrate like a domain specific

instructions and terminology into their

agent workflows and so really the point

of these last couple slides was just to

remind you of like just to to always be

looking ahead in the space because

you'll get something set in stone and

like that doesn't mean it's going to

work like things will things will change

and things will break but that's like

kind of the beauty of it is because

everything's so new and like we're we're

we're on the front end of this curve

right now we get to do a lot of

experimenting and just understanding

what works and what doesn't and

specifically what works for you and what

doesn't work for you because you know

everyone operates a little different but

just sort of a reminder to always stay

looking ahead but that is going to be it

for this master class where we talked

about prompting specifically for

prompting AI agents um you know if if

there's any doubts still I know we

started to get a little more advanced at

the end but there's definitely still a

lot of room for learning more about

prompting so any doubts um feel free to

join my free school community the link

for that is down in the description um

you can hop in there and shoot me a DM

and I'll I'll get back to you as soon as

I can I love to help you guys out and I

love to meet you guys so yeah um I

really appreciate you guys making it to

the end of this video if you did and

I'll see you in the next one so thanks

guys

in this video I'll be walking through

step bystep how to build out this rag AI

agent system that uses postgress and

super base what we're building today is

a little bit more improved version of

other rag Builds on this channel and

we'll dive into why you want to set up

your foundation like this in order to

have a rag system that's a little bit

more production ready and make sure you

guys stick around to the end of this one

because I'm going to go over some tricks

in setting up the workflow so that

anytime a new file is created it's

automatically going to go into your

super base as well as if you update any

of those old records it's going to

replace them in your super base so that

you know you can always trust the data

that you're talking to

so here's the rag agent that we'll be

working with today if you're unfamiliar

with the term rag or you've just sort of

heard about it it stands for retrieval

augmented generation and it's as simple

as the agent here's our question it has

to go out somewhere to retrieve that

information then it takes that

information back generates an answer and

then gives us that nice clean answer so

retrieval and generation are kind of the

two main parts of retrieval augmented

generation you can sort of just think

about it as if someone asked you a

question and you're not sure so you go

and Google it and then once you

understand the information you give them

back back a response but anyways here is

the system we'll be building today

here's a look at the old one that uses

window buffer memory as well as pine

cone so I'm going to break down you know

why I think postgress is better than

window buffer memory and we'll talk

about the differences between super base

and pine cone but before we do that

let's just hop into a quick

demonstration so I've already went ahead

and uploaded this document to our Vector

store which is just information about a

fake project called project Mountain so

we're going to hop in here and we'll ask

the agent what are the action items for

project mountain and who are the parties

involved so we'll send this off we'll

watch it take place and as it's going on

I just wanted to mention real quick both

of these workflows that we'll be going

over today will be available for

download in my free school Community

Link for that will be in the description

you'll just download that Json you'll

come up here and then you'll import from

file and you'll have the stuff up and

running ready to go and if you're

looking to take a automations a little

further and you want some Hands-On

learning experience and help then feel

free to join my paid Community Link for

that will also be down in the

description and then if you're sort of a

small business or you're looking to have

me Implement these systems for you have

me build them out for you then please

book a link in my um website which will

also be linked down in the description

but let's take a look and see what this

um agent was able to respond to us with

so it said here are the action items for

project mountain and the parties

involved um as follows so we have

collect feedback samples we have Sarah

doing that we have metrics which will be

John it's giving us due dates as well

and then it's basically just summarizing

everything that's going to be going on

within this project and sort of the

timeline going on with it um so we can

go into subbase real quick and obviously

here's the quick vectorization of the

project mountain and then we also have

our post Cress memory in here where we

can see the human asked what are the

action items for the project Mountain

who part is involved and then we can see

the AI responded with this information

so that's sort of how this is going to

work um real quick before we get into

the actual step by step we have this

interface obviously where we're talking

to the agent and then we have this

workflow that's going on in the back end

which is um automatically putting stuff

into super base based on um a Google

Google drive folder and then also

anytime a file in there is updated it's

also um updating that record in super

base as well as deleting the old record

so that we're only interacting with

relevant upto-date information all right

we're about to get into the step by step

so if you want to skip this part feel

free but I'm just going to break down

the difference between postgress window

buffer memory pine cone super base at a

really high level so first of all why is

postgress going to be better than window

but for memory the first thing is about

data safety and persistence so postgress

SQL is sort of how we're putting the you

know the chat memory like we just saw

and it's going to keep your data safe

even if nadn or your system restarts

because when you use the window for

memory it's sort of temporary and then

it's going to wipe everything when

closed so even the window buffer memory

is super super easy to set up because if

you can see in here if we unconnect this

and we go to window buffer memory that's

all it is it's no credentials all you're

going to do is set your context window

length but you know in postgress you

have to connect your credentials and

make sure everything's set up but it's

still not too difficult but that's one

of the advantages of the window buffer

memory second thing about postgress is

that it's scalable for Big Data so it's

going to handle large data sets more

efficiently and you're going to be able

to search through them using powerful

tools like indexing um which is

obviously very important for rag

workflows especially once you get more

documents and more things um to chat

with and then finally easy integration

and long-term use post gr postgress SQL

is going to work seamlessly with n 's

databases it's obviously got nodes that

are going to support multiple users and

it's just going to be really reliable

and you know future proof as you sort of

add on to these workflows next we're

talking about real quick super base

versus pine cone obviously I've been

using pine cone a lot and it's great so

we're just kind of breaking down the

difference so first of all the purpose

super base is sort of a backend platform

with um it also has built- in relational

databases whereas pine cone is sort of

more of just fully managed on Vector

databases um which is really good at you

know their Vector search and similarity

queries for scalability subase is going

to be better for small to medium scale

Vector storage because they also have

those relational queries and relational

database um Integrations as well whereas

pine cone is going to be more large

scale Vector searches billions and

billions of vectors you know different

indexes different um name spaces to

search through that sort of thing

hosting subase can be self-hosted or

used as a manag service while pine cone

is going to be sort of a sass so there's

no self-hosting option there and then

for the use case to base ideal for um

you know relational data metadata Vector

search while pine cone is more for the

like I said large scale Vector search

with sort of minimal operational

complexity so now that we understand

that um I hope that makes sense as far

as you know future use cases when you're

trying to figure out what to use here

and there what to plug in but now let's

get into that step-by-step build all

right just to open up a new workflow the

first thing that we're building out here

is the rag agent so we're going to come

in here obviously and grab an AI agent

we will leave this one as a tools agent

and as far as system prompt um for now

we will just basically say your helpful

assistant you will use the vector

database

to retrieve relevant

information and respond to the

users query um and for now that will be

simple enough cuz the only tool we're

really plugging in is um you know the

vector store so we we'll leave it as

this for now um we're going to connect

our chat model open AI um I'm going to

use 40 mini for this case it's um you

know it's it's powerful while being a

lot more cost effective than 40 um and

for this use case it will be fine you

know as we're sort of just demoing but

you know as you get more data you need

to search through and more complex

information you could probably go to for

or um you know Claud so from here we

have memory obviously we talked about

the difference between um window buffer

memory and then postgress so we're going

to be doing postgress in this case

and you need to obviously connect to

your account so what you're going to do

here is create a new credential you'll

come in here and you'll see that you

have this information to configure which

is definitely a little more daunting

than um setting up window buffer memory

but it's not too bad so let's hop into

super base so that we can get this

information we need so if you haven't

created a superbase account go ahead and

do that real quick so once you're in

superbase it's going to prompt you to

create a project so you're going to come

in here you just need to name your

project you need to give it a

password um make it

stronger okay need to be even stronger

than that okay and then you have to

remember this password obviously so you

can copy it want to put that somewhere

safe because this is going to help you

set up stuff in the future um I'll just

going to leave this as default and then

we'll hit create new project okay it

will probably take a few minutes to set

up your project as you can see up here

it's setting it up still but you can see

some things like um we have our API keys

so obviously we'll use this later when

we're setting up the super super base

Vector store tool within nadn but we're

waiting for it to set up some

information as you can see it just went

through okay so once you got that

project set up you're going to go down

to the left hand side click on Project

settings you will go to database right

here and then you'll have this screen

pulled up and this is the information we

need to set up the postgress so we can

see host we're going to grab that real

quick Copy it over paste it into host we

will go to um our Port grab that and

then this is going to be down here at

the bottom we'll plug in the port right

here um what else do we need the

database should always be postgress so

we need to grab our user which will be

right here we will paste that into there

and then the password as you can see

that's just um the password you typed in

earlier so let me do that real quick and

once you put in your password hit save

and then you'll see connection tested

successfully let me just call this one

real

quick demo so we have this set up here

and now once that's configured we don't

really need to change anything else here

the table name is just going to be the

table that goes into um our super base

that we can look at our chat history so

we can leave that as is and then context

window length just how many interactions

the model is going to be looking at for

context so five should be fine if you

want to bump it up to 10 or 20 you can

do so let's just go with 10 for now and

that's basically it so we have our

memory set up every time we talk to the

agent and the agent talks to us the

memory will be put into our super base

um in a table called NN chat history I

think it was so now let's set up the

super base so obviously we're going to

be adding a tool and we're going to type

in Vector store we can see Vector store

tool right here we need to name this so

we will just call this um what are we

pulling in Project data so I'll just

call this projector

data we will also do the same up here

and then we need to obviously describe

what this tool is so it's going to

retrieve information

about the projects and so that should be

good for now um we've got project data

now we need to obviously connect to

model we're going to go with for minu

once again and then we're going to go

into Vector store and we're grabbing

superbase and we need to set up these

credentials as well so we'll click

create new credential we need to get a

host and a service R secret so back in

um subbase you might see host here this

is not what you're going to grab you

want to go to the leth hand side go to

Project settings you're going to click

on API and then up here this URL that's

going to be the host so you copy this

you'll paste that right in there and

then in here you need to click on for

your service Ro secret you'll click

reveal you'll copy it paste that into um

you know obviously this section right

here so let me do that real quick okay

we got the huge service R secret po

pasted into there we'll hit save should

go green we're good to go and let me

also just rename this one demo we got

the credential set up and now obviously

the operation is in this case we're

retrieving documents but now we need to

set up the table so if you come in here

you will have no results because this

current project that you just connected

to you haven't set up the table yet yet

so what we're going to do is click on

docs right here it's going to pull up

the NN docs and then we have a super

quick start for setting up your vector

store so you're going to click into this

and we have this chunk of code right

here all we're going to do here is hit

copy we'll go back into super base and

we're going to go to our SQL editor over

here on the left side we'll paste this

in that's all you have to do is paste it

in you could go in here and change stuff

if you want the table to be named

something else if you want to change

some of these matching criteria but I

don't touch anything you're just going

to hit run and you should see success no

rows returned so now once we go into the

table editor we will refresh and we

should see right here a table called

documents so this is our documents um

Vector store that we'll be putting

information into we'll get records

filled into here that we can look at

once we actually put documents into it

so that's there and then also another

one right here will pop up that's the

one that will be ended in chat history

and we can see what we've been been

saying to the agent but anyways back in

NN now we need to choose the table we

should see not yet so let refresh and

ITN real quick okay now that we

refreshed it we should be able to come

in here see our table which will be

documents we're going to grab that and

then we need to add an option of query

name and leave it as match documents so

we're good to go here um all we need to

do now is set up the embedding so we're

going to set up um text embedding three

small which is kind of the default right

now so we've got that set up we'll hit

save um if you've watched some other

videos with pine cone when you're

actually setting up your index you will

see an option to choose the embedding

that you want in your vector store so

that's when you'd set up embedding three

small and then you'd want to choose that

one in here as well but in sub base you

don't actually go through that process

of manually setting that up but we're

going to do embedding three small so

hopefully um not any confusion there but

this is going to be it as far as the

agent um you know there's no information

in there so if we said like what are our

projects looking like it's obviously not

going to return anything because we

haven't built out that workflow that is

going to um so it actually went and

searched but it's not going to return

any actual information it seems I'm

unable to retrieve information about our

current projects so now we need to go

through the process of you know actually

putting information into that Vector

store okay so in this workflow we're

going to start this one off with a

Google Drive trigger um we'll come into

Google Drive the trigger is going to be

on changes involving a specific folder

so we'll grab that you need to set up

your credentials um I've walked through

this in multiple videos early on um also

in my NN master class but if you don't

understand you're basically just going

to go in here you can click open docs

and it will walk you through exactly how

to set up your Cloud account um you know

set up your your credentials your o

consent screen that kind of stuff and

it's it's super simple so you go into

there do that the first thing we see is

that once this trigger is active so the

workflow is not active yet so it won't

be doing this but when it when it is

active every minute it will be checking

in this folder so it's going to be

looking for changes involving a specific

folder which we will choose projects

oops projects as you can see in here we

have my folders called projects with

project mountain in it that we used in

the demo and then we're looking for a

file created so anytime a file is

created this will go off and then the

logic will take place to upload it into

Tu base and as you can see right here

we've got project mountain right there

so this is the correct folder and we

know it's working and so we can move on

to the next step which is going to be we

want to set the ID from from the um file

that's being pulled in we want to make

sure that we have the the ID of the file

that's that's coming through so that we

can download it and then we can also put

the ID into the metadata of subbase so

that later when we want to update a file

we can grab that metadata in order to to

delete those records and then upload the

new one so in here we're going to be

doing a string we will just call this

file ID and then we're going to drag in

the value so you have to look through

you know all the information that's

coming back and it may may look

intimidating so we're just going to

close out of this stuff what we'll be

looking for is near the bottom um we're

looking for the spaces ID so you see an

ID right here permission ID you're not

going to grab that one that will not

actually link to the um correct document

and if you want to make sure you're

doing it right we're going to grab

space's ID but if you want to make sure

you're doing it right you can go to the

Google Doc um that you're actually

pulling into that um folder and in the

URL you will see this ID so that's how

you know that it's referencing the

correct document and also later if you

did the wrong one you'll be able to tell

because when we download it's not going

to work but if we test the step we

should see the file ID is coming back so

we're good to go here so now we actually

want to download this file so we're

going to do once again at Google Drive

um and then we're going to go down

Within file actions to download a file

so grab that um so obviously we're

downloading a file here and this is

where you know typically you could

choose from a list to grab all the files

or grab a specific file you want but in

this case it's going to be dynamic

obviously based on what's coming through

so we want to grab by ID and then this

is where we can grab the file ID earlier

that we set in order to um you know grab

the right one and if we test up we

should see the actual binary coming

through of that um document and so now

we see this binary information and

that's how you know you got it right but

also what we want to do here is ADD

options Google file conversion and we

want to convert Google docs to text you

could also do PDF but we're going to do

text here so as you can see right now

it's coming through as binary which is a

doc extension we test this again and it

will come through as um text so if we

view it we should see actual text

information coming back rather than that

binary okay we've got the text and now

we actually want to extract that so

we're going to grab an extract from file

node we're going to go down to extract

from text file which is right here here

and basically just want to test the step

and we should see that now it's coming

back as actual data that we have in NN

and then from here all we need to do is

push that into the super base Vector

store so we're going to add an option

here we're going to type in super base

and we don't want to do super base we

want to do super base Vector store we'll

use superbase later but for now we are

just going to be doing add documents to

Vector store we need to set up our

credential once again um so we put that

in there because we've already set that

up we're inserting documents we are

inserting documents to the table called

documents and then for options you want

to add options and then just leave that

there um because it's just going to

match the documents and it already has

that function put in there so you don't

need to touch it that's all we need to

do and so obviously now we need to add

our our our document loader so in here

we're doing Json we're just going to

load all data input and then for

metadata this is where it gets important

because we want to grab the actual

metadata from or sorry we want to put in

the file ID like I said so lat L we can

reference it so if we go to schema we

should be able to grab the set ID right

here which is coming through Json file

ID and actually this is not correct um I

think I just need to update my my cloud

instance but um when you put something

Json dot whatever it is that means that

it's going to reference whatever

currently most previous node that it's

coming from so this is trying to look

for file ID within this extract from

file which obviously that's not there

all we have would be json. data so um

actually let's see if we did json. dat

it would come back with the the the

project the text that we extracted so

that's not what we want what we need to

do is we need to get the file ID from

this set ID node over here that we

actually you know this is where we

grabbed that file

ID so in here typically you should be

able to just drag stuff in and it should

be fine I think this is just a bug right

now because um it's going as

Json so what we need to do is reference

the nodes so in here we type in the

curly braces we can see we have

different noes

we're looking we're looking through the

set ID node and then within there now we

want to look for the Json or actually no

it should be item. Json

dot move this so we can see do file

ID okay now we can see we we're getting

the actual file ID back and this is how

we want it because now in the metadata

of our super base we will see a file ID

so um that should be good we've added

metadata we want to add a recursive

character text splitter um if if you're

looking for more information about text

Splitters then please go watch my end

Master Class um I walk through sort of

the difference between the three options

that we have for text

Splitters um and then our embedding once

again we will be doing text embedding

three small so at this point we have

this first part of this workflow set up

for when a new um file is created within

our folder so if you you know we got a

new project we WR wrote out a project

brief and then we drag it into this

folder called projects once this

workflow is active up here it would

automatically grab it and put it in so

let's test this and then we should go

back into our table which is right here

it's empty um there we go it just popped

through so now we have these three

vectorization of this information as you

can see um we've got like the the

information right

here and then if you go into the

metadata each of these we should see a

file ID so before it would have just had

all this information The Source The Blob

type but now we've um make sure that we

put in file ID so that later we can

reference it once again so we've got

this also you can see the chat history

um which is earlier we asked what our

projects looking like and it was unable

to get anything so we've got that and

now we have data in there um and so you

know we could go chat with this agent

actually yeah let's just do that real

quick we'll go back to the rag agent

where we currently ask what they're

looking like and now we will say give me

an overview of project Mountain because

that's the one we just put in there so

now it will'll be obviously

understanding our question question

going to the database to grab that

information it's retrieving it now it's

generating an answer right here

generating an answer and then we can pop

back into here it's updating our

um is it not going to be in here yeah

there it is um it updated the chat

history and now we see it's an AI power

tool being developed by Summit

Enterprises it's giving us goals

features the team composition um all

that kind of stuff and if we go back

into super base we should see in our

chat history once we

refresh now we have this action we just

had right here give me an overview of

our projects or project mountain and

then it gave us the

overview so that's how that works and

now we just need to set up the second

part of this workflow which is going to

be if a folder or if a file is um

updated it will change the information

so we're going to add a Google Tri a

Google Drive trigger once again we'll go

down to triggers and we'll want

onchanges involving a specific folder

once

again same thing we're grabbing the same

same folder and instead of watching for

file created we'll just be looking for a

file updated so let's real quick go in

here and just say file

updated we will come in here and just

make this

one new file so we understand what's

going on in each one um let's also just

organize this we'll call this this is

the actual node that's

downloading the file and then we've got

extracting from file and then putting

into Su base so

yeah let's get working on this this

workflow now so we've got our file

updated

um let's actually

just no for now it's fine so we'll make

a change later and we'll see but we

fetched test event and it's going to

grab project Mountain once again um from

here what we want to do is grab a sub

base and we're not doing Vector store

this time we're doing actual sub base

and so that we can delete a row within

our table so we're going to set up the

credential again we're going to be

deleting a row we're going to be looking

through documents um and then we want to

build this as a string and now we have

to type in how we want to make sure that

it's how sub Bas should be looking for

which rows to delete okay so in here um

it's going to be sort of a filter but it

might look a little little Cody so what

we're doing is

metadata because in

subbase we're going to be looking

through the metadata right here

obviously and then in the metadata we

want to look for oh sorry we're in chat

history

in the metadata of um these Vector

vectorization we're looking through the

metadata to look at the file ID so we're

going to be saying like within metadata

look for file IDs that equal this and if

they equal that then delete them so

metadata we're going to do a dash with

two arrows um or greater than signs and

then we're going to say file ID because

that's what it's going to be looking for

and then we're going to do equals sorry

equals like period and then we're going

to go with two asteris two stars and

then change this to an expression and

then whatever is going inside of these

two stars is what it's actually looking

for so we're going to once again we need

to close down to grab the file ID of the

document that it's looking for once

again don't go to permissions ID we want

spaces ID so we'll pull this in right

here and it comes in it's just json. ID

and it has the correct um information

right there so all we're going to do is

go back in here we see that there's

three um rows that have that ID we're

going to come back into here and then

test the step and if we did this

correctly we should get this this is how

it should come back so that's good it

has three items because it deleted all

three of those those rows and now we

switch back into super base you can see

that they just disappeared so this is

good now every time something's updated

it's going to delete those old ones so

that we can download the new file and

then put the new file into superbase so

that we're only interacting with ual

accurate information so we'll save this

next step here is that we want to grab

the um the IDS so we're going to do

another set node and once again we're

just mapping out the actual file ID

again so that we can reference it later

at this point it's pretty repetitive so

we're going to grab it call it file ID

and then do right here so as you can see

it's referencing the node called file

updated because if it was just to do

Json it would be looking for

that's actually a great point if we just

did json. ID Let's test this real quick

so we can see it's pulling back the

actual IDs but if we just did json. ID

it would grab this ID right here so it

would be grabbing the ID of the it would

be grabbing basically the row ID of the

vector um database so we don't want that

so make sure you specify what node

you're looking

for and so now if you can see we have

three items coming back because there

were three rows so what we want to do

here now is limit because we only want

one to come back so all we need to do is

one keep the first item test that now we

have one ID coming back rather than all

three um not sure if it's like

completely necessary but it keeps things

cleaner and then you're only trying to

download like one file so that's why

we're doing that um but anyways from

there we want to actually download the

file not download we want to grab a

Google Drive node right here we're going

to download that file and this is pretty

much the exact same thing as the

previous one with an

ID and edit Fields we're grabbing in

this file ID so perfect it's referencing

the

node and we'll hit test upep so now we

can see the project Mountain this would

be the updated folder or sorry updated

file once again we want to do file

conversion text run that again we should

see the actual text coming through as we

can see now it's a text folder or text

file and now we've got this we also

could have easily just copy and pasted

this node down here which probably would

have been the smarter thing to do but

um nobody's perfect so anyways download

file

two so we've got this and then it's the

exact same thing so we can this time

we'll just copy and paste this node down

here to extract from a text file um

we'll run that we can see the

information coming through and then

honestly I think this also can just be

duplicated as well because we're just

doing the exact same thing as long as we

have um this is the only thing I think

we need to change

so um

we're grabbing it from let's see okay so

we just want to call

this set ID

2 and so this one right now is looking

through a node called set ID which

obviously there's no information there

because it's looking through this one so

now we need to make it say in this case

you'll be looking through set ID number

two so if we come in here and we just

add a number

two we should be fine um can't determine

which item to

use maybe it's just because it hasn't

ran let's okay let's try something we'll

run

this and now there's an error

okay let's just try it again we'll do it

manually

so anyways why is it doing that why is

it doing that

okay bear with me here okay so now we're

grabbing set

id2 it's working so what do we do item

Json file

ID no do we not name it the same thing

file _ ID oh okay maybe it's because we

want to maybe grab it from limit because

it's just limiting one let's try

that why does it do that when I

okay delete that we're going to go from

limit and we can just maybe say

item.

json. file ID okay perfect there we go

now we're getting the correct ID back

that we want to put into the metadata

once again um we'll hit save and now

we'll run this again although yeah so

there's nothing in there right now we

run this again and we should see um

three new vectors pop into there let's

go and see if we can see it

live um we might just have to give it a

refresh yeah we'll give it a

refresh there we go so we've got these

um three new Vector stores so the first

ones were one two three deleted those

now we have

456 and we can see in here we' got the

metadata so it's all working as it

should

um and this is really it so one thing I

wanted to mention is you know ideally

you would also

have some sort of you know a node down

here where let me just show you so a

cool option would be if you wanted to

have another trigger down at the bottom

which is going to be changes involving a

specific folder You' grab that same

folder um once this loads

up I think I'm overwhelming my computer

with with um super base information

but um let's see we grab a

folder anyways my point was it'd be cool

if there was like a file removed file

deleted that way you could just you know

delete folders once a Project's done but

also maybe it's good to give a summary

of like a project that's done or

whatever it is but there's probably use

case where you wanted to remove stuff so

in that case you'd have to probably

manually go into your super base delete

those vectors you could also just update

your file and say like this project has

concluded or this is no longer relevant

or whatever it may be and it would

obviously update that but the point

would be you you'd grab the ID and then

you just have a super based thing to

delete it and then it would just

literally just be those two nodes so it

would be like a delete row down here and

then maybe like a you know at the end of

these you could have a

notification you could at the end of all

of these workflows have a notification

that said like okay new file was created

and added to subbase and then it would

just like text you that same thing over

here blank was updated and deleted and

then reuploaded to superbase and then

down here was like project Mountain was

deleted from superbase so you could

always you know add some more stuff off

of this and this one would just delete

the file and then that would all all it

would do but I guess a workaround for

this could be you could have like a node

that is always running to compare the

files or the folder and then you would

just see if like a comparison doesn't

match up with this one then it would

delete whatever like isn't syncing from

superbase so that would be like just a

quick workaround but um maybe in the

future they'll have just an integration

in Google Drive where you can just just

do that right away so anyways we're

going to make this workflow active and

we're going to test out some stuff

so got it so this workflow is now active

it should be looking for within this

folder right here if anything new is

added so I'm going to make a new

document real quick We'll add it in

there and then we'll watch the execution

happen Okay we're back with a new one

this one's called project snow um we

were going to put this one into the the

folder I don't know if you can tell but

um yeah it's almost winter and I'm

looking forward to skiing so that's

what's top of mine but anyways project

snow right here we're GNA drag that into

projects so now in this folder we have a

folder or we have a new file just got

created just got put into the the what's

it

called the folder so here's that

execution we grabbed in here um project

snow which should be I always have a

hard time finding this anyways we'll go

to

Json project snow I might have scrolled

too far once again sorry about that um

you know what never mind we we'll see it

we'll see it later so set ID downloads a

file extracts from file now we can see

the the project briefest project snow

and then it got put into super base

we'll come in here refresh this we

should see 789 so now we've got um these

new ones with their unique IDs in there

um so yeah let's go over to the rag

agent and we will talk to um the agent

about project snow we'll

say um what is Project Snow's budget

that's simple enough we'll come in here

and see that the Project's snow budget

is 30,000 so that was obviously a very

simple use case um there we go project

snow budget is 30,000 so let's go back

into project snow let's change the

budget

to um let's just say we have no money so

now we we've changed

this we will go to the project folder

refresh that and we should see now it

just got ified and we will go back into

here and wait for another execution to

come through of the um the updated

file okay so as you can see it's running

right now um we'll take a look at that

in a sec so it already succeeded let's

click into this and now we can see it

went through the file updated path it

would have deleted this old record

uploaded the new one and let's look at

sub base sorry I was about to drink

water and then it happened but let's go

look into sub base and see what happened

okay so originally we put project snow

into here they were IDs 789 as you can

see 789 was deleted and it was replaced

with 10112 and they still have our file

IDs in there so now we should be able to

go back into the rag agent and say

um what is the budget

now and it should say something about

that we have no money which is

unfortunate but you know at least we

know we're getting accurate information

the current total oh sorry it's looking

for all so what is the budget

for project snow so that this would

probably have to do with you know

prompting and the way that we have the

memory set up because you would assume

that it would know that it's referencing

project snow but I don't currently have

any access to specific budget details

for project snow if there's anything

else you'd like to know or other

projects you're interested in let me

know so let's see if we can actually

look at what came back from superbase so

the system says use the following pieces

of context to answer the user's question

it's pulling information about products

know if you don't know the answer just

say that you don't know don't try to

make up an answer so that's how you can

um you know try to limit that

hallucination but then at the bottom you

can see budget we have no money so

that's why it came up with this answer

just basically saying we don't have

specific budget details but yeah that's

about it for this one hopefully you

found this valuable as far as looking at

you know super base and post guest if

you haven't explored these tools before

um also you know the workflows will be

downloadable in the free school

Community Link for that down in the

description if you're interested in

going a little farther and getting some

more Hands-On learning please um reach

out to me about the paid Community we'd

love to have you in there um see you on

some live calls stuff like that and then

once again if you're looking for help

actually implementing these sort of

solutions into your business or if

you're run an agency that sort of stuff

please reach out book a call on my

website and let's talk about how we can

work together but thanks for watching

this one that's all I've got um hope you

guys found this one valuable of course

and I will see you guys in the next

video

I'm going to quickly give you an

introduction to what automation is what

n8n is and how that fits into this

ecosystem of uh Automation and the AI

tools that are kind of moving into space

and what the future looks like so

automation refers to basically using any

kind of a technology or any kind of tool

to perform tasks with minimal human

intervention that's kind of the overall

gist of uh what automation is and the

goal of automation is to save time

reduce errors and really kind of

increase efficiency because if you're

doing repetitive works that's where

automation comes in to remove those

repetitive tasks and make it predictable

right so automation could be used in

business in marketing in customer

support and pretty much in every single

industry nowadays because of these AI

tools that are becoming more and more

powerful so there are two types of um

automations there's the process

Automation and then there's a task

automation uh process automation

basically refers to automating any kind

of complex workflow like for example

invoice generation would be a good

example of what a complex workflow might

look like but on top of that now with

these AI uh tools that are being

introduced in the market you can make

extremely complex Automation and then

there's also the uh task automation

which means this will be automating

simple and repeatable able task right so

for example sending a followup email uh

chatting with customer support all of

these all of this is something that can

be very easily repeatable and therefore

very easily uh automated so that's kind

of the overview of what the concepts of

automations are and um what that space

is so there's been a huge obviously

influx of no Code and low code uh tools

that have come into this space because

of AI tools right so uh no code tools or

local tools like and it and really

empowers users that previously didn't

have technical knowledge to really get

involved and bu build workflows because

of the fact that these user interface

for these tools have become extremely

powerful where now you don't need to

have any background and coding where

before in order for you to build these

automation using these uh uh technical

tools you need needed to know how to

code otherwise there was no way for you

to be able to jump in and create these

automations or workflows yourself so

these introduction of these low code and

no code tools that have been coming in

the market lately because of AI that has

really removed this barrier to enter in

this space and that's what is extremely

exciting as we move forward in the

future so what these no Code and low

code tools do they really speed up

development and uh like I mentioned it

kind of removes that gap between the

technical and non-technical users uh

where before it was very difficult for

non-technical and Technical user to

collaborate but now thanks to these

great tools you can actually collaborate

with developers with technical people

because you have a very low barrier to

entry so that's where we kind of come to

nadn so nadn is an extremely powerful

tool um it is a no code automation tool

but there's obviously a lot of uh

customization options so if you are good

at coding or if you know coding already

you can even build more complex tools

right but the barrier to entry to

building these automation tools have

completely been removed because of the

fact that tools like NN are in the

market and in my opinion NN is the best

tool when it comes to building powerful

automations and building powerful AI

agents specifically uh because of the

fact that they are focus is more

shifting towards building AI agents and

they're releasing uh really great um

tools on top of their existing

Integrations that they have to make it

really really powerful so one of the

biggest features in my opinion uh that

nadn has compared to other tools that

are out in the market is the fact that

you can actually self-host all of this

self hostings gives you huge Advantage

when it comes to the privacy of your

data right because a lot of companies a

lot of um individuals are very hesitant

to share their data with third- party um

apis or third party uh apps therefore

the ability to self-host nadn and your

instances really gives you that peace of

mind and full control over your data and

therefore privacy so that's kind of a

huge uh benefit there um and then ALS on

top of that uh andn is also extremely

flexible uh which means that it has

existing native integration with other

apps but on top of that it gives you

also access to uh tools that you can

connect to third party apps that it

doesn't have integration with um another

biggest thing in my opinion is the cost

when it comes to these no code or low

code tools that are out there in the

market and zapier make.com are kind of

um in the same space and there's other

tools as well but these are kind of the

most popular ones when it comes to cost

honestly it's none of these tools are

even close to NN so tools like zapier

and make.com they actually charge um per

per operation versus uh n then actually

charged per workflow and again I I

understand if you're new to this you

this might not make any sense to you but

just to show you kind of the difference

and again these charts and this this

data is Tak directly from uh nen's blog

and I have this link that I'll I'll put

in the description below so that way you

can check out and read the whole blog if

you want because they go really do a

good job of explaining why ident stands

out when it comes to cost even if you're

using their um Cloud app it's still

extremely cheap but if you use this as a

subul option that becomes even more

cheap right and like I said we will

explain and explore those things further

down but this was just uh an idea for

you to get an understanding of what this

space is and why and it and really

stands out compared to the other tools

and also a huge difference between in my

opinion between nadn and the rest of the

tools that are in the market when it

comes to the automation space is their

AI tools they have really shifted their

focus on AI they definitely are moving

and they're understanding that the

future of uh these tools are moving

towards uh building AI agents that's

going to be specific to different tasks

that will sit on top of these large

language models and that's where really

going to focus and explore the power of

ID and all right so that was kind of a

quick introduction of the automation

space and these different tools in the

next video I'm going to introduce you to

the NN app the canvas how to sign up for

the free 14-day trial nent account so

that way you can get started um and then

I'm going to do a quick introduction of

how you can start to build your own

little automations to be able to get a

good understanding before you move on to

the rest of the tutorials um so this

will be a good foundation for you to

understand and get started with

ANM we're going to go ahead and get

started with signing up for an account

for an NN I want you to start with just

the cloud account for now because they

give you a 14d trial um and that's going

to be good way for you to get started

don't worry about self hosting at this

point if you're new to nadn I think it's

a good way to get started is through

their app uh cloud account which is very

very simple so that way you can at least

get familiar with the uh with the with

the canvas with workflows and all that

good stuff so I've put a link uh below

click on that it will take you directly

here you're going to come and click on

get started so go ahead and uh fill your

name a company email just put your

personal email a password and the

account you're going to be uh putting

for example for me it's going to be AIW

workshop. app. edit and. Cloud so this

is going to be the URL um so once you do

that click on try for free and then this

will uh log you in into the account and

this you only have to do this once

because next time you come into this URL

it will automatically sign you in and

bring you to your workflow okay so once

you do that once you log in it might ask

you a question about you know what you

using an addin part go ahead and uh fill

that out and then it will bring you to

your dashboard so this is where you're

going to get started after you log in uh

it might take a couple of seconds um for

it to get online so you but it will tell

you uh when you're online it just going

to say currently online and then you can

click on the open here so just a quick

introduction here so the version we'll

take a look at that in a little bit but

this is going to be the latest version

um and I will make sure I um kind of

show you where to update your version

because that's very important because

whenever they're releasing uh new

versions they're going to be fixing

different uh bugs that might be in uh

the nodes that you're going to be using

so you want to make sure you're running

the latest version okay so let's go

ahead and click on open workspace okay

once you do that you're brought in to

kind of this workflows homepage and on

the top left left hand corner here it

says 14 Zen left in your in it and trial

so that's what it's going to look like

which is great because you can use this

for uh 14 days for free and then if you

are okay with using the cloud and you

don't want to go towards the self uh

hosting again it's perfectly fine but

anyway so just to kind of give you a

layer the layout so the workflows so

this is where you're going to be

starting to build these different

automations whether it's um agents so NN

refers to all of that as workflows and

that's what I was talking about earlier

when it comes to nnn being cheap and uh

compared to these other um tools that

are out there is because they will

charge you based on the workflow so your

workflow can be extremely complex you'll

be only charged for the workflow and by

the way that's on the cloud account not

on the self hosting because on the self

hosting it's going to be different so

for this particular um account as you

can see right now in the center it says

start from scratch there's credentials

we'll come back to what that is on the

left hand side you have the admin panel

so if you click on the admin panel this

will take you to uh basically the same

place as we were before and if you want

to update the version that I mentioned

before because right now if I go back to

my um workspace here on the left hand

side in the bottom if there's any update

that needs to be done for this

particular version that you're using it

will show up right here so if you click

on admin panel it will take you back to

that starting point and you can click on

settings here and this is where you'll

be able to see what uh version you're

running and they have several there's

like a beta that they have the latest

beta and the latest table so try to stay

on the latest table because that's

always um the safe space to be so you

have your time zone if you have a

different time zone make sure you're uh

selecting your correct time zones and um

the bottom you don't have to worry about

this for now and again right now this is

a trial so this will show you your uh

plan what you're in okay all right so

let's go back to our dashboard now so

we'll go back to open opening it and

let's go ahead and create our first

workflow so that way I can give you an

introduction of what those things are in

the bottom here so the templates and

variables and all executions don't worry

about this for now uh we will come back

to this at some other point but let's go

ahead and click on start from

scratch so this is going of be uh the

canvas basically this is where you start

with building your workflows but before

we do that I just want to quickly go on

the bottom and actually change the theme

because I like their Dark theme with

looks a lot better in my opinion but

obviously if you're using the light

light uh if you want to use the light

theme that's fine as well but the way to

change and uh change the theme Here is

you're going to come here on your next

to your name you're going to click on

these three dots go to settings and this

will take you to your personal settings

you'll see your name your uh email that

you use for this account and your

password if you want to change that you

can always enable the two Factor

authentication um I would suggest doing

that if you have really sensitive

workflows that you're building but in

the bottom right here the

personalization you click on theme they

have obviously the light theme that

which are currently the default system

but we can click on Dark theme and let's

go ahead and save this and as you can

see now the theme changes and in my

opinion like I said this is the way

better in my uh user interface or it

looks a lot better okay so that's good

now you're going to go back and this is

going to be your uh canvas again all

right so a few things to point out here

on the top left hand corner so this is

where you can actually name this

workflow and I highly highly suggest

naming your workflow whenever you're

creating a workflow because that way uh

you don't get lost and you have a good

way to organize your workflow so for

example this time I'm for this one I'm

just going to say test

workflow all right and you save it

workflow successfully created so now if

we go back to our home if you click on

home this is the first workflow that

you've created and obviously you will

see all of your workflows down here all

right so the way to get back to your

workflow is you're just going to click

on it and it'll take you back to your

workflow the tags right here so this is

where if you have a lot of workflows

that you've created in order for you to

organize them you can actually tag this

unfortunately right now um and it end

does not have the ability to um kind of

group workflows together so the way to

do that so let's say for example if

you're building um uh accounting

workflows and you want to be able to

separate that to for for example uh from

your invoicing or from your customer

support workflows then what you could do

is just add a TX to it so for example

for this one I'm just going to add a tag

of AI agents right so now this workflow

will always have this AI agent tag next

to it so if I go back to my homepage on

the right next to the workflow as you

can see right here it says AI agent so

next time let's say I have a 100

workflows here and I only want to see

the workflows that have the AI agent

tags I can click on filter and you can

say filter by tags and as you can see my

AI agent workflow tag shows up there and

when I click on that filter it will list

all of the workflows that are related to

that tag okay all right so I'm going to

get rid of that remove filter let's go

back inside our test workflow okay so on

the right hand side here you can see

there's these three dots and then um

there's the upgrade the save the share

and inactive so on the three dots so if

you click on this this will give you

several options to download import um

another workflow into this and again

like I said we will get into this later

on we we build other complex workflows

where then you can uh actually import

that template inside uh this workflow

and it will bring everything over but

again like I said for that we will talk

about that at other videos uh and you

can always download your workflow as

well so once you build your workflow you

can download it as a Json file and then

you'll be able to uh import it or take

it with you to another um uh workflow

and be able to put that in there as well

you can duplicate this workflow

obviously and then you can always delete

it as

well make sure you're always saving your

workflow that's a really good habit to

have as you move forward and bring uh

build your workflows make sure you're

always saving it because otherwise uh

your progress might get lost if

something uh gets closed uh without uh

you doing that on purpose so share again

for now we don't have to worry about

this for now we'll come back to this

later inactive and active and again once

we build our workflows I'm going to uh

explain what this is

so in the center here uh we have the

editor and the executions so the

executions will come back later on when

we actually go through and build a few

workflows and try out uh and test these

out we'll come back and I'll explain

what executions are but you will be on

the editor section whenever you're

building your workflows all right and

then on the bottom right here so uh the

zoom to fit whenever you're uh zooming

in or zooming out you can always if you

have for example multiple connecting

nodes or multiple connecting uh

workflows that You' have built and you

want to go back and kind of zoom out and

go and see everything together you can

quickly come in here and click on Zoom

fit and it will Center everything it

will show all of the noes or all of the

different connecting apps that are

inside that workflow you can obviously

always zoom in and zoom out and then

with this one you can go back to and

reset the zoom as well uh the test

workflow button so this is where once

you build the workflow you can actually

test it using this button and again we

will go through and actually uh take a

look at how that function works so you

add the first step by either click on on

the center or right here right and again

on the next video I'm going to go ahead

and show you how to put in your first

node and build a very very simple

workflow so that way you get an

understanding uh but for this one again

this is already getting very long so I

just wanted to give you kind of an

introduction of the different um things

that are inside your canvas and how to

navigate within your canvas and within

your account once you created all right

so I will see you on the next

one so in this video we're going to

explore um further what uh NN nodes are

how the workflows work together and I'll

give you an introduction of how to

create your first step and add different

noes together or different apps together

and connect them to be able to go

further and create different automations

workflows or AI agents all right so so

we're back to our canvas this is our

test workflow as we built in the

previous uh video so we're going to go

ahead and add our first step so nodes

are the building blocks of NN you can

think of it that way right there's three

categories of nodes there's the entry

point Noe there is the function note and

then there's the exent point Noe so

there are different types of note and

and it and there's triggers that are

basically your entry points there's

actions and apps which will talk about

which are kind of the functions and then

there's um nodes that are related to

data transformation to flow to files um

and many many more advanced nodes

including AI nodes so the the way to add

nodes into your Canvas OR into your

workflow is you can click on the middle

button right here or you can come here

on the top right hand corner and as you

can see it says open nodes panel right

so you can do that or click on this it

will take you to the same place okay so

once you do that this is it's going to

open up because this is a first step

it's going to immediately take you to a

place where it says what triggers this

workflow because a trigger is the first

step that will start your workflow

there's several types of triggers

there's the manual trigger there's on an

app event there's on schedule on web

hook call there's on form submission and

again depending on what you're building

these different triggers will be

relevant to your workflow so for example

if if we just want to build a test

workflow we can click on trigger

manually and this will automatically add

that node into the center of our canvas

and now we can move this you can move a

note around by holding it clicking on it

and holding it and you can move it

around so what this does is basically

means that whenever you click the test

workflow here this workflow the first

step or this trigger is going to get

initiated on the top right here as you

can see these three dots you can click

on that you can test this step from here

you can rename this note you can

deactivate it you can copy and paste it

or you can delete it and the shortcut

here is also that you can delete this

node right from the top right there so

and on our left hand side as you can see

this kind of identifies already that

this is a trigger note and if we click

on if we put in another note you will

see that it will always have this little

lightning sign which means that this

node is a trigger note so let's go ahead

and get rid of that and add another

trigger note so on the right hand side

again you can see all these notes that

are existing so let's say you were

building a chat bot right let's you're

building a AI agent that you're going to

utilize with chat which means that you

can embed this into a website you can

click on a chat chat um note and this

will be your first trigger so same thing

on the bottom as you can see it says

when chat message received meaning that

this is going to be your trigger now and

on the bottom right here as you can see

this chat uh appears next to the test

workflow and again same thing on the

left left hand side you can see the

trigger button here meaning that this is

going to be your first note to trigger

your

workflow on the right hand side so this

is where you can connect nodes to this

particular node right so when you click

on it it's going to be the equivalent of

same as going right here and clicking on

it meaning that once you click on this

directly this will now open up what

happens next right that's what gives you

um and then gives you flow that tells

you hey add another note because we've

already had a trigger s already

recognizes that so now we can add

additional triggers so now we can do

action in an app meaning we can uh do

something in an app with services like

Google and all sorts of other native

integration it already has with uh nadn

so these going to be all of the apps

that are already there that already

exist within nadn so you can add any of

it so for example let's say I want to

add a Gmail note I could either scroll

and find that particular app that I'm

looking for or the fastest way to do

this is just quick search here right so

if I search for Gmail I can add that

Gmail Noe and now further it's going to

give me options of okay what kind of a

Gmail node do you want this to be so it

really gives you a more specific so for

example if you want to send a message

you can click on send the message and

now as you can see it will automatically

open that note so let's go ahead and get

out of this and as you can see right now

it is uh the next step that got attached

to this partic to this previous trigger

note and I can move this around

and it shows you that this note is

attached to this previous step okay so

the way to delete this same thing you

can either come here delete this note

from here or if you want to remove this

connection you can come and click on

this uh remove connection right here so

let's go ahead and get rid of this now

if I want to add let's say um not not an

app but I want to be able to add

something to transform the data that I'm

receiving from this chat message for

example I can click on data

transformation and this will open up all

of the data transformation nodes that

are available within NN uh you can add

code to it you can add date and time

edit field this is a very very useful

tool that we'll go into in detail in

later videos but you can modify at or

remove different items that are coming

in from your previous

node you can do uh different types of

filtrations you have uh splitting out of

the data you can filter a data B based

on a condition you can merge you can

aggregate so they're really really great

uh notes that they already have when it

comes to transforming your data or data

transformation you can have a flow uh

you can click on the flow um node Group

which basically gives you all of the

popular nodes that are within that

category so you can loop loop over items

you can filter you can merge items and

then obviously these other ones that are

there as well there's obviously the core

and the advanced Ai and these are uh

kind of the complicated ones but for now

we will not focus on this cuz again this

is kind of an introductory video for now

and you can always add another trigger

to this as well but that's not really

common uh but let's go ahead and

actually add another node so that way I

can introduce uh what the canvas is and

what the inside of this node looks like

so let's click on uh data and

transformation or like I said I could

always just if I already know which note

I want to add I can quickly search this

note as well so let's say I want to

search for data so once I do that all of

the notes that are related to data will

show up and I can go ahead and select

whatever I want so let's say so this

customer data store um is a aned end

training node which is great because

this gives you some prepopulated or data

that's already inside it so that way you

can interact with it so I'm going to go

ahead and click on that and click on get

all people and now as you can see it

quickly added this uh to my trigger

here if I click on chat on the right

hand on the bottom here uh this will

open up my chat window where then I can

send some form um of a data into that

particular note so let's say I want to

send a data called let's say hello so if

I click on that as you can see now you

will see that this note executed a um

chat message saying hello and this

outputed the notes so that's another uh

really cool thing from the an NS user

interfac is that you can see the data

that's coming in from different noes

just from the outside and how much data

is coming in right so from here I'm

saying hey one item is being it's coming

in from um this chat Noe it's being

outputed and and and it's being sent to

my other note that's attached to it and

and from this note there's five items

coming in so let's go ahead and click on

this note the way to get inside a note

is you can double click into it and it

will open up this note and what's inside

of it but before I do that actually let

me go ahead and um get rid of the data

that's coming in here just so we can

start from scratch there so if I want to

remove the data that's got initiated

from these different notes I can come in

the bottom here and if I click on this

little um delete button it's going to

delete the execution or it says at the

bottom deletes the current execution

data so if I do that now I'm back to

blank meaning nothing is being outputed

from these uh notes so let's go ahead

and double click on this and here this

is the the inside of a note if you think

about it that way so in the middle here

this I can move this thing around

meaning this is the note that I'm

currently interacting with the input so

this is going to be coming in from my

previous note and the output is going to

be the output of the current note that

I'm in right so my previous note I can

click on execute and this is going to

execute the previous note which in our

case is going to be our chat note I can

also click on this left hand side in the

corner if I go back here I can see it

here in a little corner here I can click

on it and it will take me to the

previous node as well right so you can

always go back and forth between nodes

when they're connected but I can go

ahead and double click on this so these

are the different parameters and the

settings for this particular node we

don't have to worry about settings in

most of the nodes most of the noes we're

going to be interacting with the

parameter so the operation for this

particular note is because this is a

training NAD training uh node it means

that it's just going to Output um a list

of people or a list of one person so if

I operation if I select to get one

person and if I click on test step this

is going to Output this result right

here okay so let me go ahead and move

this on the left hand side here and as

you can see on the left hand side here

it says when chat message received so

that trigger no Fields um because there

is nothing coming out of that input uh

from my previous

note so on the right hand corner here

and same thing by the way on the right

and left you can see that there is the

schema view table View and Json view so

let's go ahead and take a look on the

right hand side because we have some

data on our output so this is currently

our table output meaning that this is

going to show all of the data that's

being outputed from this particular note

in a table format right so it's going to

give you basically the columns and the

rows with the names on the column names

on top here so I have one piece of data

that came in or one row of data that

came in from this uh operation or the

from the output of this note and it's

showing me in the table

format there's also the Json view so the

Json stands for JavaScript object

notation that's a Json uh data format

you can see it in the Json view which it

shows you in a really neat and uh cool

way if you want to be able to interact

with this from a Json View and then

there's the schema view so this is where

you can see the output in the schema

mode and we'll talk about that in a

little bit and why the schema node is

extremely useful when you're connecting

different nodes together so let's say I

want to Output some more data let me go

back to my table view here I can click

on get all people and this limit says

five but it's actually only five even if

you add more into this it's only going

to Output five because that's kind of

the default so let's go ahead and test

this I'm going to click on test step and

as you can see now I have this five

piece of data that got outputed and

again I can see this right now in the

table view because it's showing me nice

and neat the column names the rows and

then the data that's inside this and

again I can always click on the Json I

will be able to see the Json view here

and then also the schema as well okay so

if I want to get out of this note I can

always click here and come back and see

my canvas View and as you can see right

now it says five items are being

outputed from this particular note and

same thing again I can always double

click on it and change this uh f format

and let's say I want to uh delete this

and start with my trigger note and I

want to send a piece of data through

this I'm going to go ahead and say again

hello now if I double click on this note

now I can see on the left hand side here

this is the data that's coming in from

the previous notes so I'm looking at it

in the schema view um and I can always

take a look at it from a table view or

the Json view as well so as you can see

see this is the input that's coming in

and this is the output that's coming in

or coming out from this particular node

okay and the operation of the canvas or

the node itself in N8 n is always from

left to right so you're going to be

moving from left to right when you're

building a workflow it's always going to

go from left to right meaning that all

of the inputs are going to be coming in

from the left hand side and output is

going to be on the right hand side all

right so this video has gone long enough

let's go ahead and stop this for now on

the next video I'm going to go ahead and

uh continue on this particular workflow

and we'll add a few no few more nodes

and I'll show you how to drag or grab

data from the input and do something

with that data and therefore um have a

output that's going to be related to the

input data that will be coming in from

the previous note from us okay all right

see you in the next

one so in the previous video we kind of

created this our initial trigger note

which was a chat and we also created

this customer um data store which is NN

training note all right so let's go

ahead and continue in this um workflow

that we're building here so let's go

ahead and double click on our database

here this note and as I said before I'm

going to click on test step and this is

going to Output all this data that's

coming in so now let's get out of this

so now let's go ahead and actually start

to manipulate the data that's coming in

from this node and add connecting nodes

to this so I'm going to go ahead and

click on the plus button because I want

to add a node that's going to be

connected to this node right so you're

going to click on the plus button so now

let's say I want to transform the data

that's coming in from this node and

therefore I can either search for that

particular node that I'm looking for or

come in here and click on data

transformation and you can see all of

the different noes that are available

for me uh to be able to do something

with the data that's coming in from here

so let's go ahead and add this edit

fields or set that you did there uh that

NN first so I'm going to click on this

and as you can see now if I back out it

is connected to my previous note

automatically okay so let's go ahead and

double click this one of the things we

can do and I always suggest doing it is

adding a name to each your note and this

gives you really a good organization and

gives you a good understanding when

you're especially when you're building

really complex workflows uh naming your

node is very very useful because it it

will uh give you a good understanding of

what node is doing what right so I'm

going to go ahead and for this one I'm

just going to say transform

data and if I just click on that and

click on rename it's going to change the

name of this node to transform data now

if I back out as you can see right here

in the bottom this is what it's going to

show and same thing if I want to change

the uh name of this all I have to do is

click on this double click on it double

click on this again and I'm just going

to say test

data click on rename back out and as you

can see now my um node has really nice

and clean name here so let's go ahead

and as you can see right now there's

five items that are coming in as an

output from this to this node so let's

go ahead and double click on this and

try to do something with this data

that's coming in as you can see on the

left hand side I have my input and this

is going to be coming in on that

previous video I can always click on

this and this will take me to that next

um or the previous node I can always go

to my other node that's connected to

this by clicking on the right hand

console okay so right now I have this as

Json view um I want to go ahead and try

to uh utilize my schema view to be able

to do something with this data that's

coming in and manipulate it one more

quick thing in the Json view right here

as you can see on the input you have

this little drop down and this is going

to show you all of the notes that are

connected to this note and therefore you

can have access access to them uh from

your Json view here if you want to let's

say grab something or grab data from uh

your previous node here so that's kind

of a neat little uh drop down they have

but let's go back to our schema view

here all right so this is all of the

input like I said that's coming in from

our previous node you can see um I have

the name of my node and then all of the

different items that are inside that

node and this is the previous note again

that's shown to me just like on the Json

view you can toggle between uh the notes

here on the schem of view this will kind

of list down all of the nodes on the

left hand side and I can always minimize

or maximize this by clicking on the

little arrow there okay so now let's say

I want to be able to do something with

uh this particular data that's coming in

there's several modes that this

particular node has one mode is the

manual mapping and another the Json so

if you want to interact with Json view

if you're familiar with code then you

can utilize Json view but most people uh

will be using the manual mapping here

here so this says field to set so as you

can see right here it says drag input

Fields here or add Fields so one of the

great things about edn is that you can

actually drag different items inside of

nodes and be able to interact with that

data manipulate that data change that

data or add something to it so let's go

ahead and let's say I want to drag and

filter this data or transform the data

that's coming in just by the name and

the email so I'm go ahead and click on

um grab the name and just bring it down

here as soon as I do that as you can see

when I uh dropped it here this shows me

these curly brackets and then the dollar

sign json. name so this is what nnn

refers to as expression so anything

that's inside these curly brackets are

JavaScript code right so you can always

click inside it and if you um if you are

familiar with codee you can always

always do different things with it but

let's say if I want to add additional

piece of code or additional piece of

function I can just click on just add

Dot and then all of these different

suggested functions are going to open up

for me where then I can manipulate this

via code but I'm not going to do that

for now so let's just go ahead and

remove that dot from here and I can

always expand this so if you have more

data that you're putting in you can

click on this little button right here

and this will do an expand view where

then you can now interact with the and a

maximize and with more space and again

this is going to be very very useful

when you're building complex uh nodes

and you're trying to manipulate data or

if you're adding uh prompts then this or

this view becomes really really useful

and as you can see on the left hand side

so again these are all the data that's

coming in this is my Json so I can

always drag different stuff here and

this will show me um the data in the

Json View and then the right hand side

it will show me the result of what that

looks like and you can always is you

know manipulated from here but I'm going

to go ahead and for now get rid of this

and let's go back to our uh node view

here so I can name this particular data

that's coming in right so let's go ahead

and say full

name

oops and I can specify the type of data

this is right so if it's a string a

number a Boolean an array or an object

obviously this is going to be a a string

so I'm going to leave it as string and

in the bottom right here you can see

that it shows the result of what this

data looks like and obviously this is

going to be J Gatsby because that's what

the name of this uh test data that's

coming in from this side right okay and

I can always add more stuff so let's say

I want to add the email here same thing

all I have to do is just grab the email

drop it here specify the type as I'll

leave it as it is and I can change the

name to email

okay and let's go ahead and grab the

country as well so I'm going to grab the

country same thing I'll just rename it

to Country you can always re rename this

to whatever you want and let's go ahead

and also uh maybe add this created so

that way you can see um the actually you

know what let's grab the ID so that way

you can see that this is a number so

this time ID

and I'm going to change this to

number okay and on the bottom like I

said you can see the result here okay

cool so options again I don't have to

worry about options for now because it's

is going to be a very very simple

transformation so now as you can see on

the left hand side we have these uh five

pieces 1 2 3 four five six six pieces of

information that's coming in um uh for

for a particular item and we're

transforming we're only grabbing four

pieces of information so we're almost

like filtering this data right because

we're only grabbing the name the email

the country and the ID so now if I click

on test step here what this is going to

do is this is going to Output all of

this data based on whatever criteria

that we identified here and here we

basically said hey we want all of these

data meaning all the five items that are

coming in from our previous input or our

previous note we want to Output this and

I only want to see the full name email

country and ID and as you can see the

column names now instead of the name

that was before and like I on table here

so here this is a good

view here the ID name email notes

country created all of this was coming

in and we manipulated this data using

our set node and the output is now only

four columns which we renamed it also to

full name email country and ID so now we

got all of this data that's coming in we

filtered it or we grabbed only the data

that we wanted to get right so this is

going to be the output now from this

note and if I get out of this as you can

see right now this came in and these

green tick marks it just means that the

execution was successful so if there was

any kind of error you will see it in red

here okay so now there's now five items

just came from here and five items

coming out from here however this this

time the output of this is that instead

of this five six columns that was in the

input made the mistake here get rid of

this instead of uh the six column 1 2 3

4 5 six the six columns that it was we

basically um manipulated the data and we

now only have four columns so we don't

we said that you know what we don't need

the created time and the notes field we

just want to be able to grab these

fields and therefore we have now uh

grabbed and changed the data that was

coming in from the previous RM okay so

let's go ahead and add and do something

else with this right so I'm going to go

ahead and click on plus button here and

now let's say I only want to I want to

filter this right I only want to filter

this for the certain criteria that I

want to give it right so same thing you

can click on data transformation or you

can just search here for filter and all

of the nodes that are related to filter

it will show up here so I'm going to go

ahead and you can click on filter here

with this will remove items matching a

particular condition you can have an if

node and you can have a switch node so

the switch node is that if you have um

several criteria that you're defining

then switch node is extremely useful

because this will output several types

of data based on the filtration function

that you have given but let's say I want

to use the if node so I'm going to click

on the if

nodee so now let's go back quickly just

to see yep so now it's connected so now

the the if node spits out two outputs

it's going to spit out output or a data

that's going to be coming out of this

note as either true or false so if the

condition is being met for true it will

spit out all of the data from this area

and if it's not meeting it it's going to

send that data to the false node so

let's go ahead and double click on

this so now let's go ahead and say hey

if this data that's coming in from my

previous note

right has a particular value then I want

to be able to Output that but if it

doesn't then I don't want that data to

be shown in my um output from this

particular note so for example as you

can see the country here um for this

particular um data point it doesn't

exist so now I want to say you know what

I don't want that data to come in here

or I don't want any fields that doesn't

have a country uh to be able to be

outputed in my notes so the way I could

do that is the condition as you can see

you have value one value two and

whatever the condition you define in the

middle here so now let's go ahead and um

say you know what I only want to be able

to check the data that exists and if it

does send it to the true and if it

doesn't send it to the false so the way

to do that is instead of equal to

because it's a comparison operation you

have several operations that you have uh

access to you have the string operation

if it's a number you do a number or if

it's date and time depending on what

type of data time but for us

particularly this country because we

want to filter through the country

column here this is a string so I'm

going to click on string and you have

all these operations that are available

to you through this if node but for us

let's say I'm going to say hey if this

particular set of data exists then

output it so therefore I'm going to

click on exists and as soon as you do

that this is going to now um say hey

okay the data that's required for this

particular action is needs to be inputed

here

so for the value now I'm going to go to

my schema view let me pull this out here

click on schema so now I'm going to grab

the

country and now I'm going to say same

thing again as soon as you grab these

items it's going to show you um you know

the different suggested uh operations or

functions that you can utilize within

the JavaScript code uh to be able to

manipulate this further but for now

we're fine with that so the output as

you can see the result it says us so now

now I'm going to say if the country

exists outp put this data so let's go

ahead and actually test that

step all right perfect so let's go ahead

and click on the table view here on the

input and we can take a look at this all

right so from here I have 1 2 3 4 five I

had five items that were coming in now

we filtered it we said that if the

country doesn't exist output this data

and as you can see now we have four

items because this item this zapot bble

BRS it doesn't have country therefore it

did not output that so now if we get out

of this now you can see that there's

data that came in and it's kind of hard

to see but there's data that came in

from true and then also the data that

came in from false so if I just add

something else to that we don't have to

add anything to it I'm just going to

quickly show you that this will further

show and I can move this around

here and let's go ahead and add one more

move this around here so now you have

these conditions uh that are being split

this data is being split so now let's go

ahead and test the step again if I click

on play now you can see that five items

came from this node five items came from

this node and now you have four items

that went to our true statement or our

true route and one item that went to our

false rout so this is how you can

manipulate and test um or change the

data that's coming in based on these um

different notes that come in and now I

can do something with the data that's

coming out from this note right here I

can add further um notes to it to be

able to change it and same thing with

here this will be completely separate

right because now I can do different

things with the data that's coming in

from the output of this particular node

okay all right well hopefully that gave

you kind of a further understanding of

how these nodes work and how you can

manipulate the data based on the

different filters you want to apply or

the different for nodes that you can add

to these things uh that you can further

manipulate and

change in this step-by-step tutorial

we're going to build a very powerful

agent that will have the ability to

scrape and extract realtime data from

popular search engines like Yahoo Google

Bing beu and others this is going to be

very simple to build uh but this will be

a good introductory video on how to

build AI agents with any end so let's

get started okay so I'm in my workflow

once you log in go to your workflow and

create a new new workflow um I'm going

to add the first step as a chat so our

trigger is going to be chat because

again we're building this AI agent

that's going to act like perplexity

meaning that it'll have access to this

real- time data so the way we're going

to interact with it is via chat so let's

go ahead and add the first step as chat

so you can either click here on a top

right hand corner here so I'm just going

to go ahead and first add uh first step

and then on the right hand side on the

bottom again these are all the triggers

you're going to come down and click on

chat message uh we're going to leave uh

everything as it is all right so now it

says wi chat message received so I'm

going to click on this plus button and

come down here go to Advanced Ai and go

down here and select oh actually it's

right on top right here so I'm just

click on AI agent okay we're going to

leave everything as it is again we're

going to say take from previous note

automatically and this is connected to

our chat um so that's our trigger so I'm

going to leave everything again if you

want to change the name here same thing

you have the um ability to change the

name on top but I'm going to leave it as

AI agent all right so I'm going to click

outside of this all right cool so let's

attach now um our corresponding tools

memory and chat model so for chat model

I'm going to use um open AI but you're

more than welcome to use whatever large

language model you have access to but

one thing to remember if you're using a

large language model you have to have an

API account and you have to have some

money on that API account again I've

only put like $5 on my open Ai and I've

used it a ton and it's more than enough

uh but you have access to grock you have

access to entropic uh AMA which is

integrated with with um meta's large

language model Lama so you can use that

or the uh obviously open AI chat model

so I'm going to use open a chat

model here the first thing you're going

to do if your account is not connected

this will give you um kind of it will

show you like a little error message so

you have to connect your account if

you're not familiar with um connecting

this so what you're going to do is click

on your create new credentials and

here's where you'll attach your API key

and your organization ID the good thing

about NN is that it actually gives you

um setup guide on a rightand side right

here and you can it has a link to the

doc as well so if you click on this link

it will take you directly to the docs

where it gives you a really

comprehensive guide on how to create or

attach the credentials for whatever uh

tool you you're using and in this case

um attaching your um API account open

eyes API account and again you can go to

your um open API documentation here and

this will take you to that link where

you can log in and once you log in you

can go to your API page and grab your

API keys and come back and attach it

right here and again on the right hand

side you can see it gives you a little

um summary of how you can do this by

logging into your account open your API

keys to create API key and the

organization ID if you belong to

multiple organization and that's where

this organization ID would come into

play but for now you know just attach

your API key all right so once you do

that you're going to come back and your

open AI account will be attached and

since I've already done that it's there

so now I get to choose my model so I'm

going to use gp4 because I want to have

the most powerful model and obviously

you have lots of options here um if you

want to further customize uh your gp4

again you can add things like uh the

sampler temperature um you can increase

or decrease this temperature and if

you're not familiar with the temperature

of how large language models work again

try to Google it because I don't want to

go through that explaining right now uh

but anyway so we're going to leave

everything as it is and we're going to

uh click outside and as you can see now

our openai chat model is

attached let's zoom in a little bit

there you go okay so now the next step

we're going to add our memory of course

uh you're going to click on memory here

and we're going to choose our Windows

buffer memory the buffer memory the

easiest way to put this is it gives you

it gives your AI agent access to

previous data uh while you're chatting

with it so it stores the memory in the

windows buffer meaning it can have quick

access to your previous information and

it allows it to reference and remember

the past interactions and the past um

chat history that you have done done

with that particular model but anyway so

I'm just going to click on Windows

buffer me and again you don't have to do

anything you just click outside of it

and now you have this attached so I'm

going to bring this over here all right

so for tools the first tool I always add

is a calculator so you're going to click

on tools and you're going to come down

here and click on calculator so what the

calculator does again you don't have to

really do anything here it change the

parameters or setting but a calculator

allows your AI agent to perform any

mathematical operation while you're

chatting with it so if you're chatting

with it and the AI agent needs to access

or have the skills to do some kind of

mathematical operations then that's

where the calculator comes in I always

add this tool just so it's there even if

I don't need it so all right so that's

going to be our first tool the second

tool I'm going to directly attach my Ser

API directly to API to this AI agent and

the way to do that is if you come down

one of the tools that NAD is already

integrated with is called Ser API and it

says uh Google search on the side but

again you have um I'll show you in a

little bit what Ser API is I'll explain

a little bit and why this is a good

integration to have so I'm going to

click on Ser

API all right so here again you have to

have your credential to connect with I

got rid of my credential so I could

create this live in this video so let's

go ahead and do that and I'm going to

walk through step by step so I'm going

to come here click on create new

credentials and again same thing we have

to go ahead and add our API key and I

can click on this open docs right here

and this will take me through the

step-by-step guide on how I can create

an API key and attach but it's a very

simple process so what I'm going to do

is go to um you're going to go to Sur

ai.com so this is their uh website ser

ai.com and as you can see right up front

here let me zoom in a little

bit as you can see they have several

Integrations with several languages but

the documentation so as you can see all

of these documentations they have access

to things like obviously most of it is

Google related um because they have

access since Google being the largest

search engine in the world they have all

these apis that they have access to but

they have access to things like Buu Bing

do Dogo Yahoo eBay YouTube Walmart I

mean even Home Depot uh but anyways this

just shows you that this has a huge

amount of knowledge that this Ser API

has access to and therefore once you

connect the serp API to an AI agent

that's why I was mentioning in the

introduction of this video that you're

essentially creating a perplexity

meaning that you will have the most

updated information because it's all

coming from these popular search engines

and the beauty about Ser API is that

it's not limited to the to pre-trained

um data that a lot of these large

language models like chat gbt or even

perplexity and llama are all trained

upon because obviously they have to be

trained on a base model and some times

in in the case of chat GPT for example

that data is limited to a certain amount

of time and I know they say they have

access to the internet but the

information that you get from uh chat

GPT for example on uh things that

require access to real time information

from the Internet is unfortunately not

accurate all the time so that's why

things like Sur API become so relevant

and another advantage of um having your

agent access the um or get connected to

Ser API is not only does does it provide

you the most real data but it also has

access to data like organic searches or

paid ads that Google or these other

search engines already run right so

that's what makes it very very different

compared to these um existing

pre-trained large language Models All

right so that's a little bit about Ser

API uh so let's go ahead and register

for account so I'm going to click on

register all right I'm just going to

sign up with Google all right I'm going

to click on sign up with Google

I'm going to give her access to my

account it's good to

go all right I'm signed in so let's go

ahead and subscribe so they have several

oh I forgot to mention about their

pricing okay so they have several plans

right now um on the free plan and that's

all you need to be honest but just

quickly um so here are their different

plans they have available so if you want

to you know if you are doing 5,000

searches a month then you're going to

get on developer production big data but

the free account gives you 100 search

some on and in our case that's good

enough because we're just building I'm

just building this AI agent for um for

this demo purposes anyway uh but go

ahead and sign up for your free account

and so when you come here just make sure

you're clicking on that free plan and

I'm going to click on subscribe all

let's go ahead and do ah this thing is

so

annoying all right I need to verify my

email all right confirm

email email has been confirmed sweet oh

I forgot we need to verify the phone so

I'm just going to add a phone number

here and verify this all right so now I

have my account I don't know why I'm so

zoomed in here there you

go all right so now I am in my account

and as you can see on the top here it

says your plan usage for this month 100

searches so and the left hand side again

I don't even have to add a credit card

so that's good to go okay so now let's

go ahead and grab our API case you're

going to come on the left hand side here

and click on API key and here's my API

key you can always regenerate an API key

which is what I'm going to do because

after this video I'm going to delete

this and regenerate it and you should do

that too don't share your API keys with

anybody uh so I'm going to go ahead and

copy this API key and we're going to

come back to our NN account and paste it

right

here and click on

save it says credential successfully

created all right cool so we got

connected um you can add properties so

for example if you want to specify this

to a uh the results to a country to a

device or you can have an explicit array

that you want to add so all of that

option is available for you like I said

you can do it even with a country so

like if you want to have you limit the

searches are just to uh us or some other

country you could do that and again this

gives you that optionality that things

like chat GPT uh or other large language

models don't have right because they're

um trained on massive amounts of data

that are not specific but with

connecting to Ser API you can actually

limit to um different options and you

can add these things like and even you

can actually limit even limit it to a

Google domain right so if you only want

to have access to google.com's search

results you can you can uh specify that

and have it um just be Google domain and

if you want to for example have it uh in

the US or or just explicitly train it

for English you can add all these

parameters that will give you more of

specific data that you're looking for

right so and again this is what makes

this AI agent so great because you can

add all these parameters that usually

that normally you're not capable of if

you're just using things like proxity or

uh chat gbt or uh an Tropic so for now

I'm just going to leave it as it is

let's just get rid of these and let's

test it out and we can always always

come back and um test it later on to see

if we can limit it to a certain country

all right so we're good to go here let's

go ahead and test this I'm going to come

and save this here it's always good to

save okay so let's go ahead and test

this I'm going to click on chat here so

for the prompt I'm going to try to use

something a prompt or ask it something

that's going to be relevant to um the

most updated information that a search

result will have access to versus things

like chat GPT right okay so let's say

What are the

best

restaurants actually what are the

top

rated

restaurants in San Francisco let's

say so this should um be able to pull up

the most recent rated restaurants right

because it should have access to uh

Google's search results and all these

other search engines that will provide

the most updated information all right

there you go so it provided the top

um restaurants and to be honest I kind

of agree with this because you know I

live near San Francisco so I'm these

restaurants are very popular and as you

can see you know this gives it um on the

right hand side this gives you that log

so um initially the AI agent um went and

updated the windows buffer memory used

open aai chat model and used Sur API

right and the response as you can see

came from Sur API and it updated or it

used chat GPT and updated the memory

again so as you can see this gives you

really uh updated information that

something like a chat GPT won't have

right so let's go ahead and see uh maybe

today's weather that's a good way to

check too what

is the

weather like

today in San

Francisco and I can confirm this on my

phone to make sure that it

is accurate

so it

says

65° yep it's 64 65° Perfect all right so

all right well hopefully this gave you

an idea of how to build this simple AI

agent uh on the next tutorial I'm going

to create um an AI agent that will label

and organize all incoming emails into

our inbox so stay tuned for that one I

will see you on the next video thanks

for

watching we will build a really useful

AI agent that will automatically label

all of our incoming emails and our inbox

this is going to be actually very useful

because anybody can use this to organize

their mailbox this agent will be able to

automatically recognize the content of

the emails that are coming in and

automatically label them according to

our predefined labels that we have in

our Gmail account all of the labels will

be color coded so that way our inbox is

nice and organized we're going to

utilize the text classifier node on n in

which is basically an instant of Lang

chain again if you're not familiar with

these terms don't worry I'll walk

through step by step and explain

everything so that we have a good

understanding of how this works and

therefore you'll be able to build your

own um AI agent that will be equivalent

or similar to this for your own purpose

all right so let's get started okay so

as always we'll start on on our workflow

and you'll come here and we'll click on

ADD

workflow so this time we're going to

remove our um when clicking test because

we're going to uh provide our own

trigger which is going to be a Gmail

trigger so that's going to be the first

step so let's go ahead and add our first

step I'm going to click on this button

right here and I'm going to look for

Gmail click on Gmail and we're going to

use a trigger I mean there's lots of

actions here but we're not going to use

that for now we're going to use that

towards the end when we're labeling our

account but we need to start on on

message receive so this is going to be

our trigger right so if you don't have a

credential uh let's go ahead and add

that I have already two credentials but

I'm going to walk through step by step

all right so let's go ahead and do this

so I'm going to go ahead and create a

new

credential so there's a step-by-step

guide that NN provides and if you click

on open docs it will take you through

the step by step on how to do that but

I'm just going to quickly uh walk you

through so on the right hand side I'm

going to click on Google Cloud here you

need to have a Google Cloud account um

once you create your account if you

don't have already you're going to come

and click on console

and you're going to come here and click

on a new project you're going to create

a new project obviously I have several

here so that's why um my drop- down

shows all these different projects but

yours is going to look blank so you're

just going to click on new project

you're going to say and you're going to

name your project so I'm going to do

nent test

3 organization leave as no organization

click on create so now it's going to

create your organization or your project

um and then once once you are done with

that you have to make sure that you are

on the correct project again if you have

several projects you going to make sure

that you're on the right one but if you

this is your first project then don't

worry about selecting your crack project

it will automatically go to that project

so I'm going to click on my project head

it in test three um so now we're going

to click on API and services all right

once you're here you're going to come

down and click on o consent screen uh so

if if this is your first time you need

to make sure you create a o uh consent

so for the user type if you have a

Google workspace account you're going to

click on internal but if you have a

personal uh you're going to click on

external so I'm just going to uh click

on external click on create app name you

can do name a app here so I'm just going

to do then test three for the support

email from the drop down this will

automatically pull up your email so just

select your email leave the logo as it

is the app domain you don't have to

worry about it and here for authorized

domain you need to click on ADD domain

and you're going to add and it in. Cloud

all right so that's done developer

contact information select your email

click on Save and

continue don't worry about these save

and continue again save and continue for

test users for summary back to

dashboards so now we're pretty much done

with uh creating our oot consent streen

so now here's an important step make

sure you're clicking on publish app

otherwise it's going to give you an

error when you when you want to when

you're going to log into your account so

you're going to click on push to

production and confirm it says

verification not required which is good

to go because again we're using our own

nent account so we're sure that um it's

verified already okay so now once you're

done here you're going to come to the

library and you're going to search for

your Gmail API so I'm going to search

for Gmail

API Gmail API you're going to click on

enable all right so that's done um so

now now we're going to go to our

credentials we're going to click on

create

credentials and you're going to select

oot client ID application type it's

going to be web application name of the

Cent name you're going to do n8n test

three again you can name whatever you

want so test three here's the important

part in the bottom here where it says

authoriz youir uis you're going to click

on ADD URI you're going to go back to

your account you're going to copy this

callback URI and you're going to paste

it that's it you're done so you're going

to click on

Create and you're pretty much done so as

soon as you click on your create this

going to pop up with your client ID and

your client secret you're going to copy

the client ID go back paste it

here you're going to copy your client's

secret go back and paste and now that's

sign in with Google uh appears so you're

going to click on sign in with

Google and this little popup window is

going to show up it's going to say

choose the account so choose your

account and this is where the Google

says hasn't verified this app so don't

worry about this just click on advance

and you're going to click on go to nate.

Cloud you're going to select all of this

and you're going to continue and you're

pretty much done as you can see in here

it says account connected all right so

let's go back once you go back your

account is going to get connected mine

because I already have several accounts

now um this uh Gmail account shows up

but I'm going to go ahead and actually

delete some of this because I already

have a ton in there let me get rid of

this go back let me get rid of this

too all right perfect there you go so

you're going to select your account all

right so for the poll times so this is

the mo you have several options when it

comes to this is basically trying to mon

monitor your nbox so you can monitor

your nbox every minute every hour every

day whatever you prefer and this is for

when you actually activate this um

workflow so that way it's automatic and

it will always U monitor your email I

will leave it at every minute and then

later on I'll show you exactly what this

means okay so for the event we can just

uh select message receive you don't have

a lot of options and at the bottom make

sure you click on this because if you

leave this at simplified it's not going

to um get the most proper details it's

not going to provide the most proper

details so therefore just make sure this

is not selected for the filters um don't

worry about this for now we'll filter

our own using our text classifier okay

so we're pretty much done at this point

so let's go ahead and fetch a test

event yeah this is to make sure that uh

your Note is working and as you can see

this looks like it's good to go all

right cool so for the next step we're

going to add our um text classifier

agent so you're going to click on this

plus button right here you're going to

go to Advanced Ai and in the bottom as

you can see there's several options

we're going to select that text

classifier so this is an instant of Lang

chain so let me quickly explain what

that means so in simple terms uh Lang

chain is a framework that's designed to

help developers or anybody build

application that leverages large

language models like uh chat GPT or

llama or other different models and the

goal of Lang chain is to make it easier

to integrate these large language models

into different tools applications and

workflows so it just makes um the usage

of large language models very very

simple so in this instance our text

classifier node is a instance of Lang

chain which basically utilizes a large

language model like uh open AI in our

case will attach our open a large

language model to be able to classify a

text and process it and label it into

something different so that's exactly

what we're going to do we're going to

grab all of the data that's coming in

from our Gmail trigger and use this

instance of blank chain to connect it to

the open a model and classify and label

these text accordingly so let's go ahead

and do that so that's kind of like a

overview of what uh this instance of

blank chain does so first what we need

to do is we need to figure out what text

we need we're classifying right and this

text is going to be coming in from our

Gmail trigger right so there therefore

the text to classify we're going to go

ahead and make sure you in schema and

we're going to grab our text which is

going to be the body of the email

because we want to make sure that our

classification occurs from the volum of

the email and not the uh um the subject

or anything else because you know if

somebody's sending you a lengthy email

you want to make sure that this test

classifier goes through and analyzes the

body of the text the full body of the

text understand what this text is about

or what this email is about and

therefore provide the proper label that

we're going to U categorize in a little

bit okay so from the schema we're going

to come down and grab our text right

here so you know minimize the headers

and everything else so that way it's uh

easier for you to locate this so we're

going to come down here on text and

we're going to grab this and just drag

it here so this is going to convert it

into json. text again inside these curly

brackets these are all the JavaScript

code um but again we don't have to worry

about it because we're just using this

schema to just drag and drop that's it

okay so the next step is to add our

categories and this is exactly where we

will add our labels but before we do

that let's go ahead to our email account

right so this is where you're going to

be uh creating your labels first so

let's go ahead and create create our

predefined labels and this could be

dependent on what you're doing whether

it's your business or your personal

account you can create whatever kind of

labels you want but for mine I'm going

to go ahead and create several labels

the first one I'm going to create a

label that's sponsorship and again these

are all of the um email inquiries that

are coming in in my account for my

YouTube channel for sponsorship so I'm

going to make sure that um I identify

the body of the emails that are coming

in and make sure that it if says

anything related to sponsorship that

label gets automatically added and we

you know we'll we'll do that in that

category section right here in a little

bit but let's go ahead and create all of

our our labels first so another label

I'm going to add for

collaboration I'm going to add one for

business

inquiries

okay and I'm going to add one more and

just call it others so this is going to

be all of the emails that are not uh

classified or labeled as these three I'm

just going to say others all right so

now that's done let's go ahead and

actually color code this so if you come

in the right hand here and you just say

label color so for business inquiries

I'm going to choose let's say this green

one and you could always add your own

custom color so if you go here you can

add a custom color you can add the

background color and a text but it

doesn't matter I'm just going to use

this predefined ones all right so for

collaboration I'm going to do

orange for others I'll just leave it as

that and then for

sponsorship let's go ahead and label

this this as this green color okay

perfect all right so we got our labels

now on our email account now we're going

to go back to our nadn workflow so here

this is where we add our categories so

the first category is going to be the

sponsorship category so I'm just going

to click on ADD category and we're going

to do

sponsorship you can just say sponsorship

inquiries for the description

I'm going to say emails that emails that

offer or inquire about sponsorship deals

from YouTube channel blah blah blah and

again you can always maximize this and

take a look at this um all right so

that's that and you can use uh chat GPT

or or something to come up with these

descriptions uh because you want to make

sure that you have really good

description here so that way U your text

classifier uh can properly understand

and capture all of those important

details that are inside the email so

that way it can distinguish between

these different categories uh that

you're putting in so make sure your

description is really thorough and again

that's depending on what category you

have all right so that's done so I'm

going to add another category and I'm

going to say

collaboration with

companies okay so for the description

for this category I'm going to say

emails from AI companies or related

businesses that are interested in

collaborating on projects tutorials on

content creation for the channel so you

can see it's very thorough because we

want to make sure that um our AI agent

is properly or this text classifier is

prop properly classifying uh and uh

adding the proper categories okay so the

next one I'm going to say

business let's do

General business

inquiries

okay I think I spelled that wrong Ines

there you go so for this one I said

emails that pertain to General business

related topics not specifically related

to sponsorship or collaboration such as

inquiries about the channel requests for

information and other miscellaneous

business communication so that's good

and the last one I'm just going to say

[Music]

others and then our description I'm

going to say

all other emails that do

not meet the

description of the previous

labels okay so we're pretty much done

with all our categories again you can

add whatever categories depending on

what you're trying to do so once you're

done with that here this is a little bit

of an important uh step I think there's

something going on with this particular

node that if you don't select this

option for system prom template and just

you can leave this as it is but make

sure that you select this and this gets

activated otherwise it's going to give

you an error that the note does not

recognize the proper parameter so make

sure you're selecting that okay so let's

go ahead and test this step I'm going to

click on test step says a model sub node

must be connected oh I forgot to connect

this all right so let's go ahead and

connect the model first to this right so

as you can see right here all of our um

categories have have been established

here so now let's go ahead and attach a

large language model to this so I'm

going to click on large language or

click on model and grab our open AI chat

model um create your account if you

don't have already an account go ahead

and select that and create your

credentials by adding your API keys I'm

going to select uh gp4 mini cuz I've

noticed that gp4 o is very expensive

when it comes to API calls so that's

good to go all right so now let's go

ahead and double check this um first

let's go ahead and send an email so that

way we can um make sure that this is

because again this is monitoring all of

the incoming emails that are new so

let's go ahead and do that so for the

subject I'm going to say partnership

for

Content we're not monitoring the subject

so it's not going to matter what what

this classifier is monitoring is the

body so we got to make sure that we put

the proper text here to be able to

categorize this so I'm going to go ahead

and add hi would love to sponsor your

next video on a no code automation we

believe our product aligns perfectly

with your audience let's discuss the

details so this is particularly an email

that's for sponsorship purposes so our

system should automatically recognize

this and label this as sponsorship right

here okay so let's go ahead and send

this I'm going to go to my inbox so I

sent this email right now as you can see

it's just showing inbox and again that's

because I'm using the search There's No

Label on it right so let's go back to

our workflow so now all of this is done

let's go ahead and test this stop and it

should be able to recognize that a new

email has come and there you go so as

you can see right now let's double check

to make sure that the email came through

hello we're interested in sponsoring

your upcoming tutorials please share all

right that's good so let's see what it

did uh we want to make sure that the

label uh is properly done as all right

there you go you see it says in spons

sponsorship inquiries Branch one item

okay so that looks good all right so now

let's go ahead and add another node that

will automatically label our email

that's coming in in our Gmail account

right because right now this is just

classifying it but there's no way for it

to label that email so there therefore

we're going to add another note to this

a Gmail note so that way it has access

to our email and therefore uh is able to

label that so let's go ahead and click

on the plus button here I'm going to

search for

Gmail and this time we're going to go to

message actions and we're going to say

add label to message right so we're

going to click on

this here you want to make sure you're

in the again you're uh selecting your

proper Gmail account the resource is

going to be the message not the label

this is going to be the message that's

coming in in and the operation is going

to be adding a label and the message ID

okay so this is where we need to grab

our message ID from our text classifier

right so if you take a look at the

schema here again all you have to do is

just grab this ID and put it here so now

the label name or ID we need to identify

which label is this going to and this is

where this node is going to have access

to your Gmail account and therefore it

should be able to have um all of the

labels listed here so let's go ahead and

select our sponsorship there you go

right because this is our sponsorship

node all right that's good okay so we're

pretty much done here let's step outside

and put prag this here let's add our

other labels so I'm going to click on

the collaboration tab same thing

actually instead of that a shortcut is

just to copy this and duplicate there

you

go grab

this give myself some room here

double

click add label json. ID you're going to

leave it as it is and this time instead

of sponsorship this is going to be for

collaboration okay that's good make sure

you're attaching the correct um category

to the pro to the to the label that you

have here okay otherwise it's going to

it's going to have an error okay let's

try this again I'm going to go ahead o

duplicate that's good this is going to

be for General business inquiries okay

so I'm going to

say let's select our business inquiries

that's

done and the last one keep forgetting

the last one is going to be

for others let's connect this to others

there you go that's

done um to organize this better or to

make sure that we're properly um

labeling this I like to name rename

these notes so that way understand

understand what's going on so let's go

ahead and rename these I'm going to

click on this this is going to be for

our

sponsorship okay

rename out that's good this one is for

our

collaboration

rename

done this one is going to be on

our

business

inqueries rename

done this one is going to be

others perfect

done okay so all of that is good to go

so now let's go ahead and actually test

this thing out so this is the the first

one as you can see right here it says

one item so this is the message that we

just sent right here partnership for

spell partnersh shop I said but anyway

so this is the one that was supposed to

be for sponsorship and this already got

executed uh that's why it says one item

so let's go ahead and test this out so

I'm going to click on test step they

should label this email in my Gmail

account number account as sponsorship

now so let's go ahead to back to our

account I'm going to go ahead and

refresh this

and there you go so now as you can see

the sponsorship label um has been

attached to this email that that came

through all right perfect so that worked

let's go ahead and test the others too

cuz I want to make sure um that all of

this is working so let's go ahead and

send another email for collaboration

this time so I'm going to go ahead and

type for the subject I'm going to say AI

tool

partnership hi we're launching a new AI

tool and would like to collaborate with

you on a demo video or you interested

okay so that's clearly um a partnership

um email right so our tool should

automatically recognize that and should

label it as collaboration this time so

let's go ahead and test this workflow

again so I'm just going to click on test

workflow so if I click on this this time

it should come here and perfect there

you go so now it says one item

collaboration this went through so let's

go back to our email and refresh the

page and perfect there you go so this

time it says AI tools partnership hi

we're launching a new AI tool would like

to collaborate with you on a demo video

or interested so it it correctly labeled

it so let's go ahead and test the other

ones too because I want to make sure

like I said every everything is

working so this time what you can do is

instead of testing the workflow if you

just click on inactive here so this will

um activate this workflow meaning this

will automatically monitor your inbox

every minute and therefore automatically

label all these different emails that

are coming through so let's go ahead and

do that so I'm going to send another

email this time this time it's going to

be for business inquiry so let's go

ahead and do that I'm interested in

learning more about your services and

pricing could you provide more

information so again this is clearly a

um email that has as the body for

business inquiries right so because our

Ed in workflow is already live so it

should be able to um automatically label

this I it's going to take a minute or so

because obviously here uh our trigger is

saying that we going to monitor it's

going to monitor our Gmail account every

minute so therefore um it should take oh

there you go it came through so it says

and it correctly um labeled this as

business inquiry right inquiry about

your channel hi I'm interested in

learning more about your service and

pricing blah blah blah all right perfect

so again this is live right now so let's

go ahead and try one more cuz we want to

make sure that if it doesn't meet any of

these categories it should be able to uh

label it as others so let me go ahead

and type another

email just wanted to say thank you for

your tutorials they have been really

helpful so I'm going to click on send

all right the message is sent so now

like I said we'll just wait and uh it

should come through and it will

automatically it should automatically

label this as others because like I said

it doesn't meet um the category for any

of these other three therefore it should

label this properly as others so let's

go ahead and wait a little bit all right

there you oops uh it said business

inquiries that's a wrong label let's see

what we did here maybe wait him let's

see what we did wrong here so if I test

the workflows all right so let's go

ahead and click on

this and ah see this is where I made a

mistake so in the label name I put

business inquiry this should have been

others so we go back and where's others

right here there you

go that looks good now okay let's try

this again so this time it should let me

test the

workflow should go

here perfect that worked let's go back

just refresh all right great there you

go I mean the reason why it's has two

labels is because it already labeled

this as business inquiries because we

made a mistake there so let going get

rid of

that go

back this time let's try again let's try

it

again I just wanted to say thank you for

your toys they've been really helpful

blah blah blah it's good click on send

this time it should label it properly

because again now mistake was earlier I

had put business inquiries for this uh

other label or in the category so let's

go ahead and wait for that to come

through so let's go ahead and refresh

and perfect there you go so it worked

now so as you can see all these labels

are now working according to what we

identified or what we uh categorized

here self-hosting has a lot of

advantages first the fact that you will

have complete control over your data so

if you're worried about U privacy issues

or if you're worried about leaking your

data to third party app and you don't

want to use the cloud account so

self-hosting will be a great option for

you um so Docker is actually the

preferred method U by the nnn community

and a lot of other folks because it

gives you a lot of advantages and

control over how you can run and

self-host it along with other

applications so let me quickly explain

what Docker is for those of you who are

not familiar with it if you're already

familiar with it please feel free to

script this but I just want to quickly

introduce what Docker is and why this is

so beneficial when it comes to

self-hosting Inn so essentially Docker

is just a platform and it's extremely

popular uh platform in the developer

community that allows you to package

application and all of their dependen

dependencies into one standardized units

which they refer to as containers so you

could think of it as a tool that

packages all of your application like

nnn and all of its dependencies whatever

it needs

all into one single unit called the

containers again NN and all other

applications have a lot of dependency

that it comes with such as libraries uh

system tools and settings so what Docker

allows for you is to put all of that in

one container or in one unit and then

you can basically deplo deploy this um

and run it consistently across other

platforms so that way if you want to

self-host yourself in a cloud account in

a cloud provider then you can do that

and it will to behave exactly just like

it would be in your locer machine so

when it comes to nnn and self-hosting

the reason why docare is so beneficial

is because it really simplifies the

process of getting NN up and running and

because it bundles all of the necessary

components into one package so that way

you don't need to manually configure

anything or worry about any kind of

issues or environments uh that you might

run into so that's what has a huge

Advantage when it comes to the

Simplicity and the process of running

idence on your local computer and then

another big Advantage is the portability

meaning that um when you deploy Docker

in other environments so let's say if

you want to um deploy it on a another

hosting platform um what this will do is

will make sure that it consistently

behaves the way it will behave in your

local computer and then another thing is

the isolation of each container meaning

that these containers run independently

of each other uh meaning that if uh if

you have several operations or several

application and it then would operate in

its own isolated environments and again

this uh removes any conflicts or with

other applications that might be running

so that's what gives it a huge Advantage

ensuring it's really stable and reliable

and another big Advantage is the SC

scalability so as you scale your

operations in nadn a Docker really will

allow you to uh scale and deploy

multiple containers based on what your

needs are right so this really makes it

simple to handle increased workloads and

if you're creating complex uh workflows

and automation this really allows you to

be able to scale as you go without the

need to configure or manually change any

of the settings so that was kind of the

overall gist of what uh Docker is and

how that helps you when it comes to

self-hosting NN so let's go ahead and

get started um and install Docker

application the desktop application on

our computer and then we'll go ahead and

run NN through the docker application so

the first thing you need to do is you

need to go over to

doer. and you need to download it for

your machine so um whatever you're using

whether using Windows Linux or Mac make

sure you're downloading the correct

version one important thing if you're

using Mac make sure you're the newer

ones especially the uh M1 M2 M3 chips

make sure you're downloading this

version and not the Intel chip because

this is not going to work otherwise so

I'm going to go ahead and double click

on this it's going to download my

application so once you do that you're

going to go to your downloads and then

double click on doer. DMG and once you

do that it's going to ask you a few

questions to install and once you

install that then you can go over to

your applications and then uh initiate

Docker I've already done that so I'm

going to go ahead and open the docker

desktop application all right so once

you do that this is what it's going to

look like so this is their uh desktop

application it has a really nice user

interface let me get rid of that all

right let me maximize this so that way

you can see this really well all right

perfect

so this is what the initial it might

give you some uh tour but go ahead and

skip that but you will have containers

images volumes builds we're going to

focus on images and containers actually

before we do that let's go ahead and

create a folder so that way we can put

all of our nend data into that folder so

that way uh we can keep track of the

data that we use all right so I'm going

to go to my finder so go to your

homepage and right click new folder and

then we're going to call this nn-

data all right so right now the folder

is empty all right we're good to go here

okay so let's minimize this so now I'm

going to come to my images and we're

going to go ahead and click on search

images to run so here what we going to

do is search for NN io/ NN I've already

done that but let's go ahead and do it

we're going to type n8n

io/

n8n okay and the first one as you can

see right here it says 100 Mill plus 293

Stars so make sure that you're

downloading this image because otherwise

it's going to give you something not

downloading sorry you got to pull this

um so make sure that you're on the

correct one and I'm going to click on

pull and once you click on pull now as

you can see it's loading so now this is

going to pull all of that data um into

your local desktop app and and it will

be saved under the images tab and again

we'll take a look at that in a little

bit so now that you have the correct

image download here so now you can see

here it says the size and now on the

right hand side here it says run so for

the first time when you click on run we

need to set a few optional settings so

once you click on run it's going to open

up this popup where it says run a new

container optional settings you're going

to click on the right hand side here

you're going to put a container name cuz

otherwise it will select a random name

so I'm just going to say n8n container

Das container so that way I can

recognize it all right so the host Port

so this is where uh you want to host

post on your local computer what port

which in a little bit I'll show you what

that means but for now just put

5678 and this will map uh this Docker

container to your local Port so that way

you can access it through your um local

machine and again like I said in a

little bit I'll show you how to do that

all right so the volume this is where

you want n it end to um store its data

so that way if uh the container is

stopped or even it's deleted then all of

your data will persist so this one

you're going to click on this uh three

dots here and you're going to go ahead

and select um the folder that you

created right so earlier we went to our

homepage and created this folder called

nn- dat so you're just going to double

click select that and click on open so

for the container pad you need to enter

slome

slash node and then slash do

n8n and then so what this does is this

ensures that uh the data the data on

your host machine is synced to and it 's

directory inside the container of this

Docker container so this basically

ensures that all of the data is saved in

the right in the correct area okay

that's good environment variable this is

optional so if you want to do any kind

of authentication this is where you'll

enter so if you want to do that you can

go ahead and like you know use J GPT to

put uh variables here but I'm going to

just leave it as it is so now that we're

done with that all I have to do is click

on run and as soon as I do that you can

see now with BR s to The Container Tab

and it runs all this stuff and then on

the bottom as you can see now it says

editor is now accessible via Local Host

5678 and this is exactly what we typed

earlier like the port so the 5678 which

means that now on the port in your local

machine the port 5678 you'll be able to

have access to Ann so I'm just going to

copy this and go to a new

tab come here on top and paste

it and there you go so now you can uh

set up your email account so as soon as

you uh paste that in your local machine

you'll it will it will take you to the

form where now you will have to set up a

new username and password and again this

has nothing to do with your uh cloud

account so therefore there is no

migration here go ahead and enter your

information I'm going to go ahead and

enter mine okay so once you do that

click on

next and now you have to just customize

the n then it'll just ask you a few

question go through it software the

service there VI I'm just going to

say oh whatever it doesn't really matter

myself it's

fine Google get

started all right so now it presents you

the blank workflows and again it's the

same environment or the same user

interface just like if you were to

access from your cloud account you have

your templates over here you have your

accounts uh you have nadn your

credentials and start from scratch means

that now you can just jump into your

workflow and again same thing you have

ability to access everything from your

Local Host here um your Advanced AIS AI

agents whatever you need all of this

will be accessed uh one thing is if you

want to import your workflows from your

cloud account go to your cloud account

come to the top right hand corner here

and you're going to click on download

and then you can come back here and

click on import from file and then you

you will just basically select that

downloaded Json file and then that will

import all of your workflows here and

then obviously you have to um add your

credentials because it's not going to

migrate over the credentials because now

you're using your local machine to run

everything and that's pretty much it so

if you already have a bunch of workflows

on your cloud account you can migrate

them over very easily all right so now

let's go ahead and actually um stop this

so that way you see um how that works as

well so now if you are done with your

workflows and you want to stop uh the

container that's running all you have to

do is come to the container and then

right here it says stop click on this

and it says stopping n8n as you can see

in the bottom here and it stopped and as

you can see now there's that option of

play button that appears so now if we go

back to our local host and refresh this

or enter this again reload now it says

that this site can't be reached because

obviously our um Ed end container is not

running so if you want to run it again

you'll come back click on

start and now it says running right

right so go back to your tab and

reload and there you go so that's that's

kind of the beauty of kind of setting it

up once for your account so that way

you're not going to be able to you don't

have to log in there again because we

didn't set any kind of authentication um

so this just makes the process really

really smooth so on the next uh tutorial

what I'm going to do is go through uh

setting up the self-hosted AI starter

kit so this is going to be basically

similar to what we did earlier but now

we're going to use our our um command

line um because we'll be able to install

everything within our local machine

including olama and quadrant which olama

is um a software that gives you the

ability to run um and interact with

large language models that are open

source like meta AI llama languages on

your local machine we can actually

download these large language models on

our local machine and through um llama

we'll be able to interact with them and

then also quadrant is another Vector

store database uh that you can self-host

and be able to therefore interact with

everything within your local environment

so we'll go ahead and do that tutorial

next because this will give you like an

entire package uh for self hosting your

AI

workflows if you wanted to run AI

locally and build amazing AI agents all

from your machine this tutorial is going

to be for you we're going to build this

amazing AI agent that's going to utilize

all open-source AI tools including the

quadrant Vector store that's an open-

Source Vector database we're going to

use several large language models with

the AMA platform and we'll be able to

interact with this AI agent using our

chat model we'll be able to upload our

own documents and immediately interact

with it using the vector database this

is going to be a great video you're

going to learn a lot about how all these

tools connect with each other all

locally through your machine so you can

build really great agents so make sure

you stick around till the end because

this is going to be a very very useful

tutorial all right let's get started all

right so first thing you need to do is

head over to N8 n's uh GitHub it's

github.com n8n iio you will scroll down

and you'll come here and click on the

self-hosted AI starter kit so here they

provide you all the guide depending on

what machine you're using so if you for

example have an Nvidia GPU go ahead and

follow this but if you using Mac then go

ahead and follow what going to do down

here which I'm going to use because I

have a Mac so we're going to basically

utilize this right here my goal is

always not to use any code at all uh

because obviously there's a lot of

people who get a little intimidated when

they see code so that's why I try to

keep it as low as possible therefore

we're going to mostly use the docker

desktop app um to be able to download

everything we need but for this step we

have to just clone uh this GitHub replay

so all we have to do is copy that and

come to our terminal

here and all you have to do is basically

paste

it and this is going to download

everything okay let me zoom in a little

bit there you go all right so that got

cloned so now the next step is you just

need to CD into that folder that got uh

created okay so I'm going to press enter

all right so now we're inside that

folder Let Me Clear again all right

great um so before we move to the next

step let me quickly uh pull up my desk

toop Docker app so if you see right here

right now I have no images here and no

containers so that way you can see that

it's empty right now and then as soon as

we uh go through and enter this we'll be

able to uh see that all of those

containers and images is going to show

up on our desktop app so this is always

a good way um to double check and make

sure everything is getting loaded

properly all right so now that we're

inside this self-hosted AI starter kit

the next step is to be able to CD into

it we already did that and now we just

need to click on Docker uh copy this

one go back to our

terminal and again let me pull up the

desktop app here so you can see it side

by side

and paste so Docker compos profile CPU

app this is going to run um all of the

different Docker containers that's

required for this AI starter kit in your

profile through your CPU so you're just

going to press enter and now it's going

to run and pull the different containers

and images that are inside this

including the AMA post grass and8 end um

and then the quadrant Vector database as

well all right perfect so it looks like

we got everything as you can see on the

right hand side we got all the four

images that was inside that um starter

kit and on the containers tab you can

see right now it says the self-hosted AI

starter kit and includes uh the quadrant

postrest AMA and N perfect and then same

thing on um our terminal here as you can

see it downloaded everything that we

need and right now it says Local Host

disc is 78 you can access this from

there okay perfect so now we're pretty

much done here okay so now uh let's make

sure everything is running so if

I yep it looks like everything is good

to go here everything's running so let's

minimize this for now we can copy um

this or just go to Local Host 5678 so

let me go ahead and do that I'm going to

say Local Host

5678 if it's your first time uh this is

going to pull up and ask you to sign up

for an account um but if you have

already logged in through this Local

Host before then it's just going to ask

you to sign in so I'm just going to go

ahead and sign in okay you're going to

enter your email and password and you're

going to sign in all right so now at my

Brank workflow here so let's go ahead

and change the name here

to local AI kit all right so now the

first step we need to add a chat trigger

so let's go ahead and do that I'm going

to search for chat and chat trigger

perfect so here's one difference that

we're going to have compared to other uh

AI that I've built before uh in this one

we're going to give our chat the ability

to upload files so what you're going to

do is come on the options click on ADD

field and you're going to click on allow

file uploads so what this is going to do

this is going to give this chat the

ability um to add documents or add files

from right here on the right hand side

as you can see now we have this little

like plus sign with a document there

because we will be uploading our own

documents into the vector database

through the chat model and I'll explain

that a little bit more all right so now

that's done all right so the next step

is going to be adding our Vector

database so I'm going to search for

vector and as you can see right here

there's several uh Vector databases but

the quadrant Vector source so this is

the one that we're going to utilize so

quadrant Vector store is a open- source

uh Vector store that you can utilize uh

so if you go to their website that they

show you all you can see all the details

um they have uh you can click on pricing

um and they have as you can see right

here quadrant Cloud starting at zero so

you can sign up if you want but we're

not going to worry about it because

we've already installed quadrant through

our AI starter kit but it just gives you

a good overview of what uh this CN

Vector store is and why make it makes it

different compared to other vectors so

it's like the pine cone Vector score

that I've used before all right so so

your credential is going to be

automatically loaded here because of the

fact that we're running everything on

Docker right so therefore it's going to

have everything loaded there for the

operation mode we're going to be

inserting documents in this so we're

going to click on insert um and for our

Cardon collection we're going to do by

ID actually and we need to go back and

actually test this real quickly so let's

go ahead and attach this let me double

check click there so now let's just go

ahead and add a chat okay this is going

to give me an error but that's fine I

just want to um showcase how to add this

chat in there so now as you can see on

the left hand side I have the chat

message received so what we need to do

is we need to add our collection by the

chat ID because we need to provide the

ability for a user to upload their own

document through the chat window so

that's why we need to grab that session

ID of that chat that's going to be

inputed into this quadrant Vector store

where before for example in my previous

video that I did using the pine cone

Vector database I added a uh step before

this with Google Drive where we would

grab the document from the Google Drive

and upload it into the vector store but

this like I said is going to be

instantaneous meaning that a user can

upload a file themselves and it will get

added to the vector store and then they

can interact with it all right so once

you grab that that's good to go so we're

going to get out of this all right so

now let's add uh the embedding and

document loader to this so you're going

to click on embedding so you have

several options obviously to add the

embeddings but uh you can utilize the

open AI but that's not going to be local

of course but the whole point of this

video is to be able to utilize all local

resources so I'm going to use the

embeddings olama so again same thing

your olama account will automatically

get uploaded here because you're using

um the since it's all part of the same

same same container so it's going to

pre-populate everything for you that's

the great thing about this when you're

using this AI starter kit through your

CPU you don't have to worry about adding

or connecting you new credentials all

right so for the model I've already

uploaded embedded models in this so in

this account of mine I already have

these but I'm going to show you exactly

how to add a new embedded model from the

AMA platform because obviously you

cannot use chat model here this has to

be an embeddings model right so

therefore we need to go ahead and add a

new embeddings so let's say I want to

add a new embeddings here obviously your

uh when you click on this account if

it's your first time this is not going

to show uh so therefore I'm going to

show you exactly how to add new models

there so let's go back to

our AMA so if you just go to ama.com

right if you go to ama.com and if you

click on models here this this is going

to show you all the models that are

available but again we need to grab an

embedding model so you're going to come

to the top and search

for

embedding

models oh I think I spelled that

wrong all right perfect there you go so

now you have several embedding models

there's this one that's very popular by

snowflake um or you can this is actually

one of the most popular ones this nomic

embedded text and in the bottom as you

can see it says the nomic embedded text

is a large context L text encoder that

surpasses open AI text embedding 8 out2

and the embedding three SP so again this

is a very useful um embedding model that

you should utilize because it's not that

large and it's very very powerful but

let's go ahead because I've already

installed this on my uh AMA I'm going to

show you something that I don't have

that I can install so let me see here

what do I have so I got the mxb embedded

large and then the noic embedded text so

let's go ahead and add something

different

go back

here there you

go okay let's see let me act the S Lake

actually there you go this is a pretty

good one but that's pretty big I don't

want

that let me add this 20 2 million

parameter one okay all right so here's

what we need to do we need to copy this

AMA pole snowflake Arctic ined right so

I'm going to copy this you can do this

several ways the coding way is to go to

your um Docker yml file so if you go

inside your NN starter kit and open it

into in a text file you can come to the

docker compos yml file and right here as

you can see it's only pulling the Llama

3.1 right so you can actually add

another line here that basically says

AMA pull snowflake Arctic and then you

you can rerun this and that way it will

actually download that model for you but

because like I said I always want to

focus on uh using least amount of codas

possible so let me go ahead and get rid

of this I'm going to show you the

easiest way to do this is through your

Docker desktop so I'm going to open my

Docker desktop you're going to come to

your containers tab if you're not

already there you're going to come and

click on as you can see right here AMA

latest this is running so I'm going to

click on the container for AMA you're

going to go to exact right here here and

we will pull that from here so all you

have to do is just paste it right here

press enter and this is going to pull

that embedded model or any other model

that you want from um your olama you'll

be able to basically do the same thing

grab that code uh make sure you're

pulling it and then just basically say

AMA pull and whatever model you want to

pull you can add it here right so let's

say I want to add another model here

right let's say I want to add

um a normal a regular model so for

example let's let me add something very

very small all right for example let's

see let's say I want to add this Quin 2

by Alibaba so I want to add let's say

this super small .5 billion primer right

so all I have to do is it says AMA run

Quin 2B right so I'm just going to

actually just copy

this and go back to my

desktop and say

AMA pull and just paste that model press

enter and now it's going to pull that

large language model that exists inside

the AMA uh platform so as you can see

it's like the easiest way to do this

because like I said you can use and

change the um Docker file inside the

starter kit but that you know that's

going to require a little bit of coding

and if you're not familiar with it then

you're going to get lost so this is the

easiest way to do this so now let's go

ahead and double check here so if I get

out of this double click on my

embedding now as you can see I have

access to that snowflake Arctic embed 22

million parameter and then also I added

this uh Quinn 2.5 billion parameter this

wasn't there before right and you can

double check go back to the video and

make sure these two weren't there we

just added it through that Docker all

right so now let's go ahead and add our

embedding documents I'm going to click

on that click on default data loader

uh we're going to select the data type

as binary load input all data

automatically detect we're good to go

there we need to add a token splitter so

I'm just going to do a token splitter

and have the chunk size be

550 okay and if you need more

information about this again you can

watch my previous video where I

explained or the video that I made about

um pine cone database where I explain

these things in detail okay so for now

I'm going to leave it at that uh so

let's go ahead now select our I forgot

to select our embedding model yeah just

make sure uh so I know we downloaded all

this but I kind of like this nomic

embedded text latest this is um the one

that we looked at earlier that said that

it's more powerful than um open AI EMB

bettered models I'm just going to select

that and it's a smaller one because I

have a you know my memory in my computer

is not that great so that works well but

again you can select whatever you want

okay so now let's go ahead and test this

thing out so another great thing about

quadrant Vector databas is that you can

actually check out the dashboard through

your local host and the way you find

that is if you go to your Docker and

your containers quadrant right here it

says it's running in 6333 so let's go

ahead and do that go

to Local Host and we're going to do 6333

SL dashboard so that's what you need

make sure you're putting the SL

dashboard there I'm going to press enter

and there you go so this is your

collections right now um this dashboard

is empty there's no collections here

because we haven't uploaded anything but

let's go ahead and do that so now let's

test this I'm want to go to chat now and

I'm going to upload a file so I've have

downloaded this BTC white paper the

Bitcoin white paper but you can do

whatever you want so I'm going to say

what is the Genesis

block which is the original Block in the

Bitcoin white paper so now if I press

enter so now what this is going to do

let me back out of here now it's going

to split this and add this to the uh

quadrant Vector database via this

embeddings Ola model so now that's

what's happening right now once this

goes through and completes you will we

will refresh the space and you'll see

that uh a new collection would have been

added so let's just wait for this to

process if your computer's slow like

mine this might take a little bit uh but

if you have a um computer that has a

really good memory and or if you're

using a GP this going to go a lot faster

but there you go all right perfect so

now as you can see uh this went through

and 13 item came came out of here so now

let's go ahead and actually let me

quickly first double check on this yep

and as you can see right now this

Bitcoin white paper that we just

uploaded via our chat got converted into

vector and to double check this now I'm

going to refresh the page and as you can

see we have um our Vector that got added

here okay all right so that's perfect so

let's go

back okay so that step is done now let's

go ahead and add our AI agent so what

what I'm going to do is click on plus

sign here go to AI agent so here what we

need to do is because uh there are two

inputs there's the quadrant Vector store

input and the chat input but we need to

connect this to our chat input right

because we need be able to interact with

the user based on the chat but we'll add

a vector store retriever in this session

to be able to have access to the vector

Store to our document that got uploaded

in the first step okay so let me go

ahead and actually actually let's go

ahead and add that first so just agent

it's going to be not a tools agent this

time it's going to be a conversational

agent right so I'm going to click on

conversational agent The Prompt you're

not going to say take from previous node

automatically because the previous node

is a quarter Vector store what we need

to do is say Define below and we're

going to define the text right this is

going to be coming in from our user from

the first uh step from the chat input so

you're going to click on the input here

and grab the when chat message received

you're going to go to Json and from here

we're going to grab the chat input right

because we want to make sure that we're

understanding what the user is asking um

all right so it says when chat message

receive. item. json. Chat input perfect

so now we're good to go here let's go

ahead and back out of this so now let's

add a chat model so for chat model we're

going to add our AMA chat

model and here's going to be the

difference so earlier in the previous

step this step we added our embedding um

and as you can see here let me go ahead

and click we added this snowm make

embedd and text but for but this one

since this is a chat model we need to be

able to add our large language model so

you can do this Gemma 2B you can do the

Llama 3.1 latest or you can do this

really small one that I downloaded there

right but let's go ahead and yeah I'm

going to go ahead and select this Gemma

2B okay and we'll select other ones

later on too to test this out okay so

we're good to go there all right so now

let's add you can add a memory so this

is where you already downloaded the

postgress uh um uh uh database

through the AI starter kit but I'm not

going to utilize that so I'm not going

to add that here but you can you can

definitely add that so I'm going to go

ahead and utilize the tool so now we

need to start we need to add a vector

store tool right because we need to

retrieve that information from that uh

quadrant Vector store so go ahead and do

put a name here so I'm just going to say

file

input okay so the description this is

going to be the knowledge base to answer

user questions right because uh this is

going to be the knowledge base that's

going to be retrieved from the vector

store the limit you can leave at four

that's fine so now let's go ahead and

add our uh Vector store here so the

vector store is going to be the quadrant

Vector store right and this time it's

going to again pre populate already it's

going to retrieve documents this time

right and then the quadrant collection

is going to be by ID so the ID you're

going to grab this this is going to be

our session ID so this is very important

you're going to click on mapping go to

when chat is received go to Json and

you're going to grab the session ID here

right because this thing needs to match

what's in our database right here so if

you go to your quadrant this right here

this is what uh let me click on that so

this is the session ID there that will

match uh right here as you can see test

ocf 28 7 let me just double check test

ocf 287 yep that's a good all right so

that's good so we're done with that now

let's go ahead and add the rest of the

stuff here I'm going to add my Vector

sto model let's just duplicate this

actually

copy

duplicate and boom okay that's good uh

but this time for this one actually I'm

going to decrease the temperature the

sampling temperature uh to zero because

we want to make sure that it's giving us

uh the accurate answer and not

hallucinating

um all right so quadrant Vector store so

the embedding same thing we're going to

add our embedding same thing I'm going

to duplicate

this and connect

this all right so we are good to go oh

one more thing I forgot here so there's

13 items as you can see that's coming

from this Vector store we want to make

sure that we're processing this once and

not like 13 times so you're going to

click on that go to settings and you're

going to say execute once all right so

make sure you do that step okay perfect

so we're pretty much done let's go ahead

and test this thing out and make sure it

works so I'm going to this time um

delete this and try this again fresh so

I'm going to add my BTC white paper here

again and I'm going to say this ask the

same question what is the Genesis block

right I'm going to press enter so now as

you can see this thing is working again

based on how fast your computer is how

fast your CPU is um how big the memory

of your computer is this thing might go

a lot quicker and it also depends on

what kind of model you're using so if

you're using a really large uh model

that's going to be very heavy on your

computer this whole process is going to

be extremely slow so you make sure make

sure you're using um the correct model

depending on what computer you're using

and there you go so this step got

executed so 13 items were sent now the

AI agent is processing this again and

this should be running once because

that's what we put in the setting right

okay as you can see this step is

complete now it's going to utilize the

vector store tool and the AMA chat model

to be able to respond to our user's

query via this AI agent so that step is

complete again my computer is very slow

that's why this is taking so long but

usually if you have a faster or if

you're using an Nvidia GPU this is going

to be super super fast all right perfect

so it looks like everything went through

uh 13 item cames out came out of here

from the vector store and everything got

processed properly and our AI agent spit

out one item meaning that's the response

so let's double check so if I double

click this as you can see it's giving us

the output the Genesis block is the very

very first block of the blockchain

network it's essentially the foundation

upon which the entire blockchain system

is built which is correct okay perfect

so that worked out and we can actually

see the logs here to make sure that this

was done properly so if we click on the

AI

agent and right now this is showing the

output so let me pull this aside if I

click on log all right perfect so as you

can see all of the tools will be utilize

the AMA chat model the vector store tool

the quadrant Vector store embedding AMA

1 and chat model and chat model so this

gives you that log of how this entire

process works and what were the

responses to come up with this reply for

the user when they ask that particular

question all right so looks like

everything worked out great again you

can actually uh utilize for example an

open AI if you see that your computer is

too slow uh just go ahead and add open

AI because you can use the oops that's

wrong one because you can

use the API as well to be able to

connect to a model like open Ai and I'm

going to use let's say this small

one copy

this

duplicate pting get rid of

this right let's go ahead and connect

this

same thing with chat

model I'm going to utilize the open AI

chat model let's

say use gp4

mini you could you will see this will be

a lot

quicker G4

mini okay so let's try this

again let's add our

Bitcoin white

paper all right we're going to say what

was the size of the

BTC what is the size of the BTC

header let's see what this

does oh I got an error bad request wrong

input Vector Dimension error expected

all right there that's actually a good

error because this this is a good point

right here because um depending on what

embedding you're using uh it it's going

to have different dimensions meaning

that because earlier I was using uh that

embedding from olama that we downloaded

so that therefore this has the different

dimensions meaning open AI uses um a

different dimension but as you can see

for the quadrant or collection here let

me go

back the size right here it says 768

right

but our error says that the dimension

expected Dimension 768 but got 1536

because this is the dimension that comes

out of open AI embedding so therefore we

need to basically get rid of this so you

can now delete

this so now you don't have anything here

so now if we run this

again this should remove that error let

me go ahead add that

up all right let's try this

again the size of BTC header is 80 bytes

which is actually correct and as you can

see on the right hand side it used all

of the correct nodes and on the right

hand side again same thing you can see

this everything would utilized properly

and now when we go to our collections

refresh this now you can see the size is

1536 right so it just depends on what

kind of embedding model you're using um

and that will split the document into

different Vector sizes you want to make

sure you're using uh if you're changing

um the embeddings uh you make sure go

ahead and delete that collection because

this is going to upload a new collection

there you can also for this chat you can

also embed this publicly so if you come

here and click on make chat publicly

available you can actually copy this uh

URL here go to Local

Host paste whoops again these are good

errors so the reason why it's giving me

that error that uh uh code 404 is

because we have to

actually run this or make this active so

if you click on active got it go back

refresh this and there you go so now we

can actually uh utilize this chat

through the window here so same thing I

can add my Bitcoin white paper here and

I can say what is a block size what is a

BTC block

size I don't know if it makes sense but

uh why not just to test it all right

perfect there you go the block size of

Bitcoin BTC toer to the maximum amount

of data that can be contained within a

single block in the blockchain okay

perfect so as you can see everything got

executed properly and you can actually

check out the executions by clicking on

all executions yeah I got to save

this yep there you go and right here

these are all the executions if I just

go through this is the latest one if I

click on view

and you'll see this one got successful

and the rest you know it shows you the

errors and the one that's went through

or not so this is a good way to uh see

exactly what's going on behind the scene

so you know the good thing is you can

embed this chat if you have a business

or something or if you have a website a

personal brand you can actually add this

to your website and uh basically have

this chat widget where then people can

interact with their own document that

they can upload uh depending on how you

know what your use

cases all right well I hope you found

this helpful again this is a very cool

way to uh run everything locally through

your machine um and use all the open

source model because again all of this

is free right because the quadon vector

database that's free we're locally

hosting NN on our machine that's free

we're using all these local uh llama

embeddings or we're using AMA to be able

to interact with these all these local

open- Source large language models

that's also free so so it's very very

powerful because it's combining all

these tools together so use your

imagination to build something different

and see how it goes let me know in the

comments below if you WR any kind of

questions or issues thanks for watching

and see you on the next

one in this video I'm going to show you

how to take a YouTube video any YouTube

video and utilize n8n Community nodes to

be able to take that YouTube video and

convert it into transcripts where then

we'll be able to utilize several

different AI agents and AI nodes and

converted and repurposed this video into

a sales enablement tool a social media

repurposing tool and also an AI agent

that summarizes the content of that

YouTube video I'm going to utilize open

ai's devday video that they made an

announcement of several products that

they released as an example but you can

use any kind of video when it comes to a

competitor analysis to be able to create

battle cards for your sales team so that

way when they're talking to a prospect

or a customer they'll have this really

great battle card ready where then

they'll be able to utilize this to do

objection handling things like hey we

saw the new model that you guys released

for whatever product it is and it seems

too complicated so you will have a

proper answer based on the video that

will be summarized using this AI tool

and we can also take the same video

transcript and repurpose it into social

media for different platforms like

LinkedIn Instagram Twitter Facebook and

individually post them and on the third

AI agent we'll be able to take the video

transcript and summarize it and send it

to a nice written email to our internal

teams and also utilize our slack node to

be able to send that summary into our

proper teams and channel so this is

going to be a very very useful tutorial

because again you'll be able to utilize

this workflow and convert it into

several use cases if you're new to the

channel my name is z my YouTube channel

and my school Community AI Workshop is

all about building incredible AI agents

using no code tools like NN in my school

Community you'll be able to get started

from the introduction to nadn to all the

way building incredible AI agents and

also you will have all the NN templates

for this particular workflow and all the

previous and future workflows that I'll

be building and the great thing about

our community is that you will be

connected to like-minded individuals who

are here to learn and are serious about

building AI agents and automations for

businesses and personal blands I'll put

the link in the description I'm looking

forward to seeing you there all right

let's get started all right so the first

thing is is um YouTube transcript is not

a note that is natively integrated with

NN this is a community note and this is

only available on if you self-hosting so

let me show you for example if I have

this is my Ned in Cloud account so if

let me you size this a little bit so if

I wanted to add let's just do a trigger

here let's say I wanted to add YouTube

right so if I search for YouTube here as

you can see right here it just says

YouTube and you can have all these

operations that are available but there

is no category here or there is no note

that will give you a YouTube transcript

just for copying pasting the URL of a

YouTube video in order to do that you

have to go and install this YouTube

transcript node where you can just copy

and paste where you can just paste a

link uh YouTube video URL and this will

be able to convert this into a full-on

transcript in order to do that you will

come here on next to your uh username

and you'll click on these three dots and

click on setting actually no I don't

want to do that let me open another tab

here so you will come here and click on

these three dots again you have to be on

a local host or you have to host this

locally in order to have access to this

otherwise this is not going to work uh

you'll click on these three dots you'll

click on settings and then on the bottom

right here as you can see it says

Community noes and again for comparing

this to our uh if you're on the cloud

account let me go ahead and take a look

here if I click on this click on setting

uh that's fine you will see right here

that that um Community notes does not

exist on a cloud account okay so just

just so you're aware so you don't get

confused but anyways so once you and a

lot I know a lot of people are doing um

hosting this NN locally so uh you should

be able to have access to this but once

you come over here you're going to click

on community nodes I already have this

YouTube transcript installed but if you

want to install a new node a community

node all you have to do is click on

install and here will you will paste the

npm package name how you're going to get

this is you will click on this browse

and this will take you to the npm

package page where uh NN Community node

package will already be prepopulated and

this is where you need to search for

whatever package you're looking for so

for example on the bottom as you can see

these are all the community packages

that are available uh via this uh mpm

package right uh but you want to make

sure again that it includes this uh NN

Community note package in advance cuz

otherwise it's not going so for example

let's say if I search for

YouTube you can see this one this is

just a YouTube transcript but this is

not for nadn so you want to make sure

you are actually uh getting the proper

Community otherwise it's not going to

work okay so as you can see right here

this is the one that you want to grab

right so if you click on this all right

there you go so this is what it says

andit and nodes YouTube transcript so

all you have to do is click or uh copy

this name or this package you're going

to come back here you're going to paste

this and you're going to say understand

the risk because obviously um you are

using a public Source because all of

these nodes are made by Community you'll

click on install and you will have this

node installed now so next time when you

come to your workflow so let's go ahead

and so if I go head over here now if I

click on ADD node and search for YouTube

as you can see right here the YouTube

transcript node is available for me and

then next to it this little box it just

says this Noe from our community it's

part of the nen YouTube nodes YouTube

transcript package okay so that's the

difference again this is super useful

because um you know there are certain

notes that commity there's not a lot of

notes there to be honest cuz I've looked

through a bunch of it but uh there are

some useful ones so if you're utilizing

that for your purpose whatever it may be

then go ahead and check that out but

anyways so what you need to do here is

all you have to do is add that YouTube

transcript and again I have just added

the trigger as a when clicking a test

work FL dep depending on what your use

case is you can actually add maybe some

kind of a web hook here that actually

monitors for example um a competitive

business that you have their Channel or

every time a new video gets posted on

their Channel then you'll be able to

utilize that and automate it right but

then you can take that video convert it

to YouTube transcript and then utilize

your sales enablement which we'll walk

through in a little bit to be able to

convert that YouTube transcript into

several other uh things that you can do

with it right uh um but yeah so like I

said you can come here and just add a

web hook where then you'll be able to

monitor a particular Channel or you can

have an HTTP request tool where you can

um have access to other different

resources but anyways for our purposes

again for this demo all I'm doing is

literally going to YouTube and this is

the open AI Dev day that Sam Sam Alman

announced GPT 40 from outside documents

or

datab GPT turbo has yeah so this

was3 let me pause this this was

announced on December 2023 so this was

again the announcement for GTP gp4 and

the different tokens that they made

available for public so what I did was I

basically

copied the URL here and as you can see C

6zk I want to make sure you know that

that's the same URL here at the bottom

right here it says 6zk right so that's

the YouTube and when you uh click on

test step what this does is this is

going to take that and convert it into

um a nice little summary here and if I

go through the table view here you'll be

able to see all of the transcript from

that video you want to make sure if you

want to return this as one text you want

to toggle this to merge text because if

you don't do this here's what's going to

happen this will actually return all the

timestamps too so if I click on

this now you'll see Welcome to our first

ever so all of these timestamps are kind

of provided here in the duration for

each one and as you can see in the

bottom here there's like several Pages

here so depending on what your use case

is you'll be able to if you want to do

this then go ahead so you can also add

an aggregate not so for example yeah so

all this data is coming in here with the

timestamps um so you can take this aggre

let's say you only want to grab from a

particular timeline um then what you

could do is put a set Noe and then use

this aggregate node where then you'll be

able to um grab all of that and convert

it into a nice little data here using

this node and again all you have to do

is put the input field name and in this

case it's going to be uh I think it was

the text yep right here is the text and

I'm converting it to um or I'm renaming

the field to data and it's going to

provide me all of that data without the

timestamps or anything like that but

anyways for our purposes um we don't

need to do that so I'm going to get rid

of this so now it's saying sending 70

items and if we go to our sales

enablement here this you can see it says

it's sending all of these different

pages and I don't want that right for my

use case um I want to be able to return

this just as a merge text so I'm going

to click on that test step and welcome

to yep perfect so that's I I'm getting

this as one merge text without the kind

of the uh array of different timestamps

with different uh text in there and as

you can see it's here it's sending this

one item to different nodes on the next

step all right so that's how you

basically uh take a YouTube video and

convert it into transcript again you

could for example let's say if there's a

product demo right so let's say you have

a product demo for a SAS company that's

your competitor so you can take that

product demo and utilize this tool so

for example let's say this a SAS

explainer video you can take this video

and um add it to U this transcript where

then you can do um other things with it

but anyways for our purposes this Sam

alon's announcement is pretty good okay

so now this is where kind of the magic

of this prompting comes in right so we

have this big chunk of text or the

transcript of the video that's here so

what we need to do is convert this into

battle cards for our sales theme for

those of you who don't know what battle

cards are it's basically a way uh to

utilize a source a resource that you can

extract and have a product feature

highlights you can have object um

objection handling um and then also

suggested responses for uh those objects

that might come from your customers and

that's exactly what the prompt here does

right so I added this sales uh open AI

node where I choose my account and again

you can watch my previous videos if you

don't know how to connect your account

the resource is going to be text because

this is what we're using here uh the

operation is going to be messaging a

model right and then you're going to

select the model in my case I selected

gp4 mini if you have a lot of so if

you're putting a large video or a video

that's very long um so for example let's

say if you have a seminar that you're

trying to summ arize and turn it into

something different you want to make

sure you're choosing a good strong uh

model so that way your open AI node will

be able to provide whatever you need but

anyways so for this particular um prompt

what I said was uh from the text

provided and the text in the bottom I'm

defining as the text that we're getting

from our YouTube transcript video

extract key insights for sales

enablement I need product feature

highlights objection handling tips

including common objections and

suggested responses because we're

telling it hey we want to be able to in

advance figure out a way that our

customers might object to certain things

so provide those object handling tips

and also provide the suggested responses

which is going to be super super helpful

especially if you've been any part of

any kind of sales team you'll know that

this is a very common practice uh and

then also I said unique selling points

so USPS are competitive Advantage

because you want to be able to um

provide the competitive advantage versus

you and whoever your competition is and

then key statistics or metrics that are

mentioned in this particular video right

and then I've said that please present

the response in the following format so

I'm providing it this format that I want

this response to be in and in my case

this is going to be these battle cards

right the first one is going to be the

product feature highlights I want two

features the objectional handling tip um

where you have a customer concern and

then what the suggested response would

be from your sales team right and then

also unique selling points and in key

metrics and I've said use Boldt headings

for each section and bullet points for

individual insights to ensure a clear

structured format suitable for sales

battle cards so I'm being very very

clear and my prompt is very structured

to make sure I'm getting the proper

output and depending on what you use

cases make sure you're adding the proper

uh prompt here and for those of you who

are part of my school Community you will

have access to uh my GPT Uh custom GPT

that you'll be able to utilize and grab

these uh prompts um from there but

anyways so here's the right side is what

the result looks like so I have this

prompt and at the bottom the text is

exactly what we want here so let's go

ahead and test this thing out so I'm

going to click on test

step and once we do that so this thing

is going to run right here as you can

see it say sales

enablement and this is the output and as

you can see right here exactly the way

we wanted it right so we said product

feature highlights let me expand this a

little bit

right there you go so um again obviously

this was a announcement uh Dev day for

GP GPT 4 uh so the first these are going

to be the two feature highlights gp4

turbo supports up to 128,000 tokens of

contacts allowing for more extensive

Nuance interactions feature two is going

to be the Json mode that they presented

so that's great right and here's the

object handling tips right objection how

does gp4 turbo compare in terms of

pricing so now as you can see right here

it's making the job job of your sales

team very very easy right so let's say

you are a competitor of open AI in this

case for example let's say Claud Claud

has announced a new feature or they

provide a new uh video that their

product team has released their sales

team could utilize this workflow or

these AI agents to be able to compare

their product with gp4 because in real

life customers their Enterprise

customers are going to ask them hey what

makes your product better than GPT 4 for

example right specifically when it comes

to pricing because that's always a

common ask so that's why you can see the

objection here a customer might actually

say this in real life hey how does your

gp4 compare in terms of pricing with

others so then the response or AI

already provides the response it says

gp4 turbo is significantly cheaper than

gp4 H with cost Direction factor three

times for prompt tokens and two times

for completion tokens very precise very

accurate based on the transcript that

we're getting again if this this is is

making the job of sales teams extremely

easy before this you have to sit down go

through the product release video or

talk to your product team and figure out

hey how do we present this to our sales

team but this is taking care of all of

that in automating the process right and

it's also giving you unique selling

points so it's Unique selling point one

and two higher rate limits for

established GPT for customer custom

models program offers tailored model

development blah blah blah key metrics

gp4 turbo can handle up to 128,000

tokens um and that's actually accurate

because as you can see that metric or

that number is actually coming in from

our context and if I look through in a

little bit I should be able to find that

there you go gp4 turbo supports up to

128,000 tokens of contact so you can see

that is not making things up right and

you can further uh establish or further

refine the prompt to make sure that it's

grabbing everything particularly from

this and however format you want all

right so now that we have all of this

and we're outputting this as Json so

that way if you want to for example say

hey you know what for my object handling

tis I want to grab this and add it to uh

my Salesforce so whatever your

Salesforce is um so if you want to be

able to for example add that to an

opportunity so the way to do that is you

can just click whatever your CRM is

right you can have Salesforce you can

have HubSpot or whatever you're using so

for Salesforce they have all these

different great functionalities like

uploading a document um um getting a

contact creating a a a summary or

getting a summary in this case we'll be

able to add this to our opportunity

right anyways but uh I don't want to

make this video too long but you can

utilize now this uh battle card and add

it to different you know your CRM you

could send an email to your particular

sales team you can add it directly to

slack as well so that way they're aware

and they're ready uh with these great

different um Tools in their hand now all

right so that was kind of the first use

case will be was for the sales

enablement now you can also let's say

this video about is about your own

product release so let's say your

product team releases this great video

of how your product works you can take

that transcript and instead of manually

doing this what you could do is add a

open AI note here and same thing you'll

go back if you want to uh learn the

step-by-step tutorial on how to add

social media content uh to uh your

platform you can watch my previous video

where I walk through step by step on

creating and attaching my link LinkedIn

account and uh block post so you can do

all of that so make sure you watch the

previous video if you want to learn how

to add your social media to this AI

agent but anyways so as far as the

prompt again the the magic here is the

prompt so I'm going to expand this real

quick just to show you what the prompt

looks like so I said from the text

provided and again the text is right

here and I'm defining the text here

create tailored social media post for

LinkedIn Instagram Twitter and Facebook

and I'm providing different contexts on

for each platform what to do so for

LinkedIn I'm seeing a professional post

highlighting the key insights with a

formal tone for Instagram a short

engaging post with the call to action

and relevant hashtags and once we click

on test this step and again obviously

make sure you're putting outputting this

as Json so that way you you'll be able

to grab the different posts and um

connect it to uh the corresponding notes

and as you can see right here it created

a nice little post for LinkedIn

Instagram Twitter and Facebook so now

all you have to do is on the next node

you can just attach this to your uh

LinkedIn account X account um Facebook

account and everything else so that's

kind of like the second um AI node here

that we added to be able to take this

YouTube transcript and do something with

it the third one let's say hey you know

what all I need to do is I want to

summarize a particular video let's say

you have a very long video a podcast or

whatever it may be right you don't want

to go through the entire podcast but you

just want a nice little summary so same

thing you will have an AI agent here and

you can add different you don't have to

add uh GPT GPT open AI models here

that's why I kind of put this AI agent

here instead of just open AI model

because uh you can have access to for

example adding a grock chat model if

you're using um an Tropics chat model

you can add whatever you want but in any

case so um for our for this particular

one oh let me

actually get out of this and add the

open ai

model4 go back all right so for this AI

agent this is going to be conversational

agent and the prompt I said defined

below and if I expand this all I said is

summarize the key points and insights

from the json. text and all I'm doing is

just grabbing this and bringing it over

here I need a brief summary of the most

important takeaways any significant

topics for theme discussion not wordy

code statistics blah blah blah right

format that response and concise easy to

Res format so now here's what you're

getting a summary of let's say a very

long video and you're sending to

yourself a nice little email or you can

put that in a slack Channel as well but

let's go ahead and test this

step and this should be able to provide

this nice little summary for us so that

way we can uh utilize this for other

notes there you go so as you can see we

have this nice little summary key

takeaways um and then also it has uh you

know kind of divided into different

topics such as as the significant themes

um and then also accessibility for AI

development for non-coders noteworthy

codes as you can right see right here

you can see that it pulls codes it say

you can now call many function that once

and will do a better uh do better at

following instructions and it also has

recommendation and points and again this

is all coming in based on our prop that

we provided here all right well so

hopefully that helped and again like I

said you can add this to your email or a

slack um or any addition nodes if you

want so this is kind of a a good

overview of what you can do with this uh

Community node called YouTube transcript

again you can completely automate this

process where you can as I mentioned

before you can have a web hook that will

be attached to this where then you can

uh be monitoring a competitor's Channel

you can um add individual YouTube links

to this uh where for example let's say

if there's a webinar or a seminar that's

very long you can utilize this this is a

great tool to be able to summarize or

turn that particular YouTube video into

something much much more if you're part

of the school Community uh you can

basically just go over here I'm going to

provide this in the template sections

all you have to do is click on import

from file and you'll be able to import

this into your own workflow where then

you'll be able to add additional loads

or uh check out for yourself how to um

customize this tool or customize this

workflow for your own purposes all right

well hopefully you found this helpful

please make sure you subscribe and like

the video I have some great great

tutorials that are upcoming and also a

few great announcement that I'm about to

make so make sure you are following that

and looking up for that thanks for

watching I'll see you on the next one

[Music]

in this step-by-step tutorial I'm going

to show you how to completely automate

your social media post using a no code

tool like NN we're going to be able to

grab any news article about any topic

and post it to our Google sheet that

will be attached to our automation where

we will have perplexity grab and

summarize the article and then we have

ai agents that's going to completely

create separate posts individually

tailored to that platform like LinkedIn

medium Facebook X slack and Gmail for

slack and Gmail we'll be able to grab

these articles and summarize it and send

it to any but internal teams or even

send ourselves a nice little email

summary of the article and what's that

article about all using AI agents all of

the templates for the tutorials that I

provide will be put it on my classroom

in the school Community where all you

have to do is basically go to import

from file and you can download that file

and have all these templates ready to go

where then when you're building these AI

agents on automations you'll have a good

reference to compare in case you on any

kind of issues if you're new to channel

my name is z my YouTube channel and my

school Community is all about building

incredible AI agents and automation

using no cold tools like nadn we have a

great Community where we have very

active members who are always trying to

lend the help to each other and solve

any issues that comes about I'll put the

link in the description for my schools

Community make sure you join us where

you'll be able to connect to like-minded

individuals and then on top of that if

you run into any kind of issues or if

you have any questions you can always

post it to our community and then

somebody or myself will be able to

respond to you right away to solve that

problem with that being said let's get

started with the tutorial all right so

I'm in my blank workflow here let's go

ahead and start by naming our workflow

so I'm just going to say social media

automation okay so the first step is

going to be us adding our Google Sheets

because our trigger is going to be our

Google sheet where every time we add in

neuro to our Google sheet meaning every

time we add a new article rink to our

Google sheet our triggle will get

activated and therefore we'll move on to

the next step so in order to do that you

have to first of all go ahead uh to your

Google Sheets you can create a blank

worksheet um I've already created one

with a few links so that way you have

some kind of a reference but basically I

created a plain blank Google sheet name

media links one column and all we have

to do is just copy and paste uh a news

article that's that we want to create

the social media post about and again

this doesn't necessarily have to be just

um news articles you can create and

utilize this for any um anything you

want so for example have an entire

article for example for medium or some

other blog post that you're used to

reading or some newsletter and basically

utilize that as a trigger where then

you'll be able to create individualized

social media post about then I going to

point it out in a little bit once people

bu this thing out but let's go ahead and

add our first trigger and in this case

I'm just going to click on this first

step and I'm going to search for Google

Sheets if you just search for Sheets it

will show up so there you go go Google

Sheets so the trigger is going to be on

row added right because every time we

add a new row then we want to be able to

have that row be grabbed or the content

of the row in this case it's going to be

that news article um be processed for

further notes all right so therefore

we're going to click on Roll added so

here you need to connect to your

credentials um if you don't know how to

do this watch my previous videos where I

show you how to connect to all of your

uh Google Drive Google Sheets all of

that good stuff uh we're just going to

leave the poll time every minute as it

is uh from the document list you're just

going to create on choose here or click

on choose here and this is it's going to

load up all of the different um

documents that are inside your Google

Sheets and in my case as you can see

mine's name is Media Link so I'm just

going to go ahead and grab this Media

Link um document and then inside that it

will process if there's multiple sheets

that you have this will show right here

but I only have one sheet and I haven't

named it so I'm just going to select it

and then it says triggered on row added

right so you can have the trigger on row

updated row added or updated so you can

select any of that but I'm just going to

say R added for now so let's go ahead

and fetch test results so let me go

ahead and actually put a brand new

article so let me search

for AI

agents

news Okay click on this article and then

I'm going to just simply go ahead and

copy the URL so now let's go ahead and

add that to our um media post or media

links document and I'm just going to

paste this all right there go cio.com s

collaborative AI agent as knowledge in

all right great so now let's go ahead

and actually test this step to make sure

that it's grabbing uh the media links

that's inside this um uh sheet I'm going

to click on fetch test

results let's see all right great so

there you go now we have four different

media tic Les or four rows and as you

can see the first one is the finance.

yahoo.com about Nvidia and the last one

is CIO sap launches collaborative AI

agents all right perfect so now as you

can see we have five it items coming out

of this Google sheet trigger so we have

our proper uh output that we're looking

for okay so now um here's what we need

to do because as you can see right now

this output is it's sending all of the

news articles um as an output what we

want to do we want to only grab the

latest one that's being added to our

Google sheet right because otherwise

this is going to process all of our all

of these articles from the from the

entire sheet so in order to do that

we're just going to put a quickly um a

simple code and again I'm not going to

utilize any code I'm just going to use

chat GPT uh to grab that for us but uh

you can click on this add no button here

and you have to search for code and you

will see you can just grab this again

don't be intimidated we're not going to

write any code we're just liter going to

copy and paste from chpt okay let's get

out of this first so now again the goal

is because right now as you can see

everything is coming out as one giant

post link right so if I go to the Json

here it's sending all of these um posts

or all of these links to this node but

what we want to do is we want to grab

the latest one that got added to our

Google sheet and in order to do that all

we have to do is literally just copy and

paste I I just took a screenshot into uh

my chat custom GPT that I've created and

if you're in my school Community you'll

have access to this custom GPT which is

called ID and FL Architect by AI

Workshop which is constantly being

trained on the different nodes that I

add and I constantly train this custom

GPT um with the different screenshots so

that way it's providing the most

accurate information for anit and

workflows but anyways I I literally

posted that screenshot of that uh node

and I said hey create um a code block

for me that basic basically grab grabs

the latest article that's added to this

Google sheet and all I have to do is

just copy code and then go back and

paste it okay so now we're going to just

literally paste this here I'm going to

get rid of this copy and paste okay

that's all so this is literally grabbing

get all the input items articles in our

case right and it's going to grab the

latest article and as you can see it

says get the most recent article

assuming it's the last one in the array

and in our case it is because every time

you add a new link it's going to be the

last one from in this list basically

right so that's what's going to happen

and then it's just going to return the

most recent article as an output for the

next mode and that's exactly what we

want so let's go ahead and actually test

this out so now if I test the step I

should be able to grab one uh link there

you go perfect so now let's go to the

Json there you go right we only grab the

latest one which is this collaborative

AI agent by sap okay perfect so let's

get out of this let's make sure we see

this correctly done as you can see right

here it's kind of small but it's five

items are coming in from this note and

then this is only spitting out one item

which is again the latest article uh but

let's go ahead and actually uh rename

our uh notes I like to always do this so

that way everything is organized so I

know exactly what is going on in my

workflow so this one I'm just going to

say media

links okay I'm just going to rename this

and then this one instead of code I'm

just going to say latest media there you

go that's good enough so now let's go

ahead and add perplexity because we want

to utilize perplexity AI to summarize

the article because perplexity already

have access to uh the internet and

that's what great thing about it is

compared to let's say if you were to

utilize a uh large language module like

chat gbt or these other ones they won't

have access or they won't be able to

access a media link just by the URL

right however NN does not have a current

integration as of October 8th so in

order to add perplexity and take

advantage of perplexity what we're going

to do is actually we're going to utilize

the HTTP request tool that nadn already

has and connect that to our perplexity

cuz then we can save that and utilize

that for our other automations uh

because once it's set up then we can

copy and paste that into other

automations that then we can utilize uh

perplexity moving forward so all I have

to do is go ahead and click on this add

note so I'm going to search for HTTP

request click on that all right perfect

so now we have our HTTP request tool

here and as you can see there's this one

media link that's coming in which is an

article about sap launching this

collaborative AI agent which we want to

utilize as uh perplexity to summarize

the article so you're going to leave the

everything as it is because we need to

head over to perplexity you're going to

come down here on next to your username

and click on this gear icon so this is

going to pull up the settings we're

going to then head over to the API Tab

and as you you can see right now I have

U 4

$482 so you need to just add or click on

buy credits and add uh a payment method

just put $5 honestly that's enough like

it could last you for a long time $5 is

going to last you for a very very long

time if you're just using it for

personal use or even for business you

know it's going to be um plenty so go

ahead and do that and then you're going

to come down here and click on generate

API key and as you can see in the bottom

I got a new API key that got generated

so you're just going to copy that you're

going to head over to perplexity API

documentation and that's just docs.

perplexity doai uh you will come to API

reference and then right here so it says

chat completion it only has this one

section here it's called chat completion

what you need to do is this API key that

we just generated you need to copy that

and paste it here by the way I'm going

to delete my API key so don't think

about copying it and that's an important

Point actually to make sure that you're

not sharing your API keys because then

people will have access to your credits

here and they can empty that out quickly

all right anyway so what you need to do

is you need to make sure you are at Carl

here right and on right here when it

says

authorization as you can see in the

bottom yours will be empty so let me

just get rid of this there you go this

is what's yours going to look like right

so you need to just basically copy and

paste that new token that you just

generated the API token oops I think I

got that

wrong go back I didn't copy it properly

copy and paste all right perfect now

that that's done and on the right side

as you can see here the authorization

bear PX and you have that uh secret key

or the API key that you just generated

so now all you have to do is go on the

top right here and click on copy and now

we can go back to our

n8n and on the top right hand corner

right here as you can see it says import

curl that's why I said it's very

important that you are making sure that

you're in the curl tab because they have

the python JavaScript and all these

other uh different sections but make

sure you're on curl so once you copy

that you'll come back to your n8n and

you're going to click on import curl and

you're literally just going to paste it

that's it right and as soon as I do that

now as soon as I click on import you'll

see that all of these existing

parameters going to get populated if I

click on

import there you go perfect see

everything got uh populated initially

the method was get the URL was empty

everything else was now all it basically

populated everything and on top of that

the most important thing is on the

bottom right here this is what kind of

came over and this is exactly what this

is right and I'm going to show you how

to change that to be able to utilize

perplexity basically inside nadn all

right so let's go back and let's take a

look at a few things because we need to

change a few things again everything

else don't touch it it's all good to go

you need to create this once and now you

can basically utilize this on all your

future automations or AI agents that you

can create all right so let's go ahead

cuz this is what we need to change right

here so I'm going to click on expression

right here because we're using Json uh

expression below here so I'm just going

to click on expression and click on this

little button you need to manually

change the prompt inside the system role

and then also the user role because this

is kind of a hack uh because U andn

doesn't have integration with perplexity

hopefully they'll add that in the future

but in the meantime this is the best

thing we can do because it's the easiest

way to utilize perplexity and you want

to make sure that you're using the

proper model that says online at the end

because that way you will have access to

the internet so right now I'm using 3.1

sonar small 128k online so we need to

provide a prompt for our system and then

also for our user and in my my case uh

we're only summarizing this article

based on this link so therefore I'm just

going to get rid of this get rid of this

and then type so I said summarize the

following article in detail cuz that's

literally all I'm doing is I just want

to have a summary of this article and we

need to identify what this article is

right so in the user content rule right

here I'm going to get rid of this and

all I'm going to do is type

article and let me go ahead and grab

grab the article now that's coming in

from our previous media okay so I'm just

going to go ahead and grab that right

here and perfect as you can see right

here now on the result it says content

article and we have the the proper link

right there that's literally all you

have to do oh one more thing actually so

you see right here it says Max tokens is

optional you want to make sure either

get rid of this or identify a token and

um I'm if you want to limit the token in

this case I want to do I'm just going to

put 500 um tokens because this is going

to be plenty to summarize a small to

medium uh length article and that's this

in majority of the cases that's going to

be plenty okay so everything else don't

touch it right so let's go ahead and

back out of this and now all I have to

do is click on test step

oops let's go ahead and test our step

let me make sure everything is good to

go yeah that's good let's test the step

and if we did everything correct this

should just summarize this article for

us

executing

node all right perfect it looks like it

worked let's check let make it sure

everything is good here Json the content

the article let me move this a little

bit here the article from CIO discusses

Sap's recent announcement at his 2024

Tech ad conference focusing on the

integration of collaborative AI agents

and introduction of sap Knowledge Graph

perfect and I'm also going to go ahead

and name this perplexity all right great

so it looks like everything is good to

go and um our article got summarized so

now what we need to do is go ahead and

uh add another AI node to be able to

split this article now into different

social media posts in order to do this

uh one of my you could use an AI agent

here uh an AI agent conversational AI

agents or uh for this particular case

what I found to be extremely useful is

just the open AI module here right so

just going to click on that open AI

module but if you want to use some other

large language models there's obviously

a way to do that via the AI agent but

I'm going to use the open AI um node

here and I'm going to click on message a

model and the great thing about this is

because we can um output the result

that's coming out of this in as Json so

then we can grab that and separate it

individually for different platforms

like the LinkedIn Facebook uh and other

social platforms okay so connect your

credentials to your opena account the

resource we're going to leave as text

operation is going to be message and

model and then you're going to select

the model whatever model you want to

select I'm going to use my uh gp4

mini all right so here's where we need

to provide our prompt and you can play

around with prompt um again same thing I

utilized my custom GPT that I've created

for NN to get a really good prompt for

this which is right here um it I just

set to generate I literally screenshot

put this screenshot into uh this N8 and

FL architect custom GPT and told it to

generate a prompt for me so what I'm

going to do is just grab

this and copy

this go back

and I'm going to click on

expression because we need to add that

article there I'm going to paste it okay

based on the following article summary

create tailor social media post for okay

that's good

enough and I'm just going to say article

summary cuz we need to provide the

article summary right and that needs to

be that can't be a constant value it

needs to come in from our perplexity

node which in our case is going to be

right here it's going to be under

choices message and content right and

this structure is coming in from it's

kind of native to perplexity uh if

you've used make.com before you'll be

familiar with this but this essentially

provides all these prompt tokens and

total tokens and all that other stuff

that was used to generate and then

obviously the model that it used right

let's go ahead and grab the content here

so all I have to do is just grab the

content right here and put it right here

and now on right hand side the results

is shown that it's uh uh taking this uh

uh article summary that we already

generated okay so we're good here I'm

going to back out uh another important

thing is you want to make sure that the

output content is done as Json cuz uh we

want to be able to grab the results out

afterwards to uh different um nodes that

we will attach for our social media post

so I'm going to click on this and now

let's go ahead and test this step

and you can always add oh there you go

perfect so now you can tell right here

that it has split everything and we can

take a look at the table view um the

Json View and the schema same thing it's

going to have a nice little separation

here because if you don't have this

output content as Json it's going to

dump everything into one output and you

don't want that because for further

notes it's going to be very difficult so

you want to make sure that you're

toggling this output content this Json

and that's why like I said I like this

open AI node compared to an agent

because for the agent you would have to

add a second step to uh edit the output

that's coming in but this one it's great

because it's already provides Us in the

format that we need for our further

notes so yeah so we're good I think here

and you know you can tell that for

Linkin it's more professional because

that's what we said it in this um prompt

that for LinkedIn for example a

professional post that highlights the

key insights of the article without the

formal tone suitable for business or

professional audience for Instagram it

needs to be short visually engaging post

what call to action and Twitter it's

going to be based on whatever that

platform requires and the same thing for

medium a longer form summary of the

article that can act as a blog post okay

great so now we can back out of this and

you can see that Medium has the longest

longest and you can further edit this so

let's say before uh you want to uh add

this to a medium or to a LinkedIn you

can add further notes to be able to edit

this to whatever you like so let's say

if you want to add further emojis or

something like that you can play with

the prompt to do that but we're good to

go for here now let's get out of this

now all right so now we have our output

so now let's go ahead and add our um

first social media platform I'm going to

uh use LinkedIn and uh let me show you

my LinkedIn here quickly if I go back so

this is my AI Workshop LinkedIn page let

me just

refresh and if you see the post these

are the post that I tested out earlier

so the post uh the last post was an hour

ago here here and this was about the

exciting world of Chip design which was

the article that's uh previous to this

uh but for this one uh the article that

we have the summary for is about sap so

let's go ahead and add that and then

we'll test it out to make sure it got

processed properly so I'm going to click

on this add button right here and I'm

going to look for LinkedIn click on

LinkedIn here and we're going to create

a post the good thing is like we can see

all of the output and the first one is

LinkedIn so all we have to do is just

grab gra this and put it here but I'm

going to switch to the schema tab

because now we can just literally grab

the post here but before we do that the

way to connect to Linkin it's a little

bit tricky um but let me show you

exactly what to do here so if you click

on uh your credentials and I've already

connected my account so but let's go

ahead and click on create new

credentials na1 has good docs and all

these things but if I click on open

docks here uh so this kind of show walks

me through the the different steps that

I need to do in order to integrate and

then however the problem is a lot of

this is focused on um this linkedin's

community managed API documentation but

I went through this a couple of times I

think the easiest way to do this is

literally stay on the standard because

if you go to the Community Management

it's going to ask you to for a client ID

and a client secret and you have to go

through and put your call back URI and

you have to go to linkedin's developer

form it's a big mess and that's what the

docs here explain as you can see it says

using Community Management or to use

this method if you're new to LinkedIn

user or creating a new LinkedIn app so

if you're new to LinkedIn or you don't

even have an app then go through or if

you're going to utilize organization

then you have to go through this uh step

by step where it says you know you have

to log in select the create a new

developer app you have to name the app

and you got to go through through all

these steps but the easiest way to do

this if you're just using this for your

personal account is go to stay on

standard and all you have to do is click

on connect my account but this will only

work if you have this toggled off

because if this organization support is

on this connect my account to this is

not going to work so you want to make

sure that this is toggled off and if you

click on connect my account this will

have a popup uh mine's already connected

so that's why it's going to go directly

and connected uh but if yours is doesn't

have that then you will have a popup

where It'll ask you that and ITN wants

to um asking you for permission to allow

to make changes on its beh have but if

you run into any issues uh then go ahead

and walk through these uh step-by-step

guide because it is a good guide but

again it's talking about this Community

Management o to but if you see that for

example you're getting an error and you

can't connect your account through this

then go ahead and create this new

developer app through the developer

Council um on LinkedIn and then go back

and go to the step again and it will

connect to your account very easily but

I'm going to go ahead and delete this

credential because I've already have

one let me make sure I got my yep so now

you will click on your LinkedIn

account resource you're going to leave

as post operation is going to be create

post is going to be as person and this

is what I was talking about if you want

to post as an organization you want to

make sure that you are connected to the

proper credentials but person name or ID

so now if you are uh account

disconnected properly you should be able

to grab that from the drop down menu and

in my case here I have my AI Workshop

here all right and that's pretty much

where you will know that your account is

connected properly so the text um here's

what we need to do we need to now grab

our post that we're going to uh put onto

our platform so I'm just going to go

ahead and grab this and bring it over

here so let's go ahead and click on this

expression Tab and it shows right here

exciting developments from saps 2024

Tech conference happens spear hitting

Innovation through integration so it's a

really good post that's already there

however let's say want to add the

article at the bottom of this post right

because right now it's not showing the

article you could ask maybe the previous

step um on the AI agent but I'm just

going to quickly do this I'm just going

to come here and say

original article

link and then what I need to do is

basically go

here because you can see that you can uh

expand this or um collapse this and I'm

just going to grab the link from the

previous from previous note which was

whoops I got that wrong yeah I'm going

to grab the link from the this node

right cuz this is the latest link that I

put yep exactly so I'm going to grab the

link from my code module here and all I

have to do is now grab this and bring it

right here and this will post the

original link to the article right all

right so that's exactly what we needed

I'm going to back out of this okay so

now um actually in the bottom here so

you have this media category right here

right so you can also put let's say your

media or your uh post includes an image

you can utilize this image right here or

you can actually even put the article

link here so if say that if the post

contains an article URL you can just

select this and you can add field and

you can either put the description or

the original URL Let's see we put the

original URL and same thing we can go

back there and grab it here PR your on

here so we'll do both we'll see like

where um where this ends up and then

based on the formatting let's say if we

don't like this one and we want to uh

keep this as it is here which is this is

what I like honestly because I have kind

of like a little title that says

original article link and then therefore

uh but we can we we can see how the post

goes all right so let's take a look at

our LinkedIn here right now let me

refresh looks like all right last post

was an hour ago all right that's good so

let me go ahead go back to my n in and

click on test step and now this should

post that article all right it looks

like everything worked out let me back

out yep it looks good so now let's go

ahead and take a look at our LinkedIn if

I refresh the page hopefully I'll see

the new

post and perfect there you go exciting

developments from sap 2024 conference

and it says AI Workshop posted this now

right this was an hour ago this is now

so let's go ahead and click on this

great there you go so now you have this

really nice ni um post that's tailored

to uh LinkedIn and again this is where

you can play around with your uh prompt

to be able to change if you don't like

the way this looks then you can uh go

ahead and change the prompt to see until

you really like the post the way the way

you originally intended but on the

bottom so this is what I was saying that

the original article link I like this

because that's where we post it but it

also has um that link here to if you

just click on it it's going to take you

that article but like I said I like this

version because um it says clearly right

there that the original article thing so

that way people don't get confused so

you can always remove this option which

is um this right here so if I go back so

if you get rid of this if you just say

none this then it will only have that

right there which is exactly what I'm

going to do all right good so we're good

there all right so now let's go ahead

and add our medium let me move this a

little bit here this is

this little too much space okay let me

put this here and let's go ahead and out

our medium uh because we already have

all these different uh let me go back

here wait a

minute oh yeah right here the output is

already separated right the output is

already separated so now all we have to

do is go ahead and add our medium

article so I'm just going to grab this

right here and search medium there you

go so we're going to create a

post okay so same thing with the medium

account so to add your credentials um

I've already added mine but you're going

to click on new credentials medium is

probably one of the easiest ways to do

this because all you have to do is just

create a access token and you'll be able

to connect your account um but you're

going to click on open docs here and

from here you're going to scroll down

and this this is the one y you're going

to click on self-issued access token

documentation and this will take you

directly to that page where it gives you

like a really good guide it is on GitHub

but um this takes you directly to that

section so you're going to go to click

on account setting page and if you

already have a media account this will

take you directly there but if you don't

you have to log in obviously so now so

let's go ahead and go to security and

apps you're going to head over to

Security and apps and then you scroll

down in the bottom right here as you can

see it says integration tokens you're

going to click on this I've already

created several tokens um so you can

revoke this and generate a new one uh

but it's very simple you just put a name

click on get token it will generate a

new token for you so then you're going

to grab that token you're going to copy

it go back to your NN and literally just

paste this and that's that's literally

all you need to do but I'm going to get

rid of this because I already have a uh

account setup there and then you'll be

able to grab this you're going to create

uh leave the resource as post operation

is create uh TI so this is where I was

saying earlier if you want to be able to

add a separate let's say a another set

node right so let's say you want to add

a set node where you want to separate

the title so go ahead and or generate a

title from the summary that you're

getting from here then go ahead and just

use the set note and you can generate a

title so that way then you can directly

post it here with a nice little title

but for now this is just for this demo

purposes um I'm just going to just

say uh basically copy and paste this

right

so let's see there you

go copy this put the title again you

don't have to do this manually like I

said create a set node where you can

grab a title from this and just that way

you can dra drag and drop it for the

content format I'm going to keep it as

HTML and then the content so this is

where you will add where' It Go the

medium post right here right oh actually

earlier I grabbed it from LinkedIn this

is a better title right here okay so I'm

going to just literally copy

this and paste

it

perfect okay and then for the content

all I have to do is go back to

schema and find medium here and this is

the post and drop it right

here right okay so so now let me go to

my medium so that way I can show you

exactly what this looks

like um my post you're going to click on

your profile and this is where all your

posts are going to be I already have

this one leg test that I did earlier but

we're going to go ahead and generate

this um workflow and then you'll see or

click on the test uh step here and this

is going to generate that article and

immediately posted there so let's click

on test

step and perfect let me back out

see one item went to LinkedIn and

another item went to medium so let's go

ahead and go back to my

medium Let me refresh the

page and perfect key insides from saf

2024 Tech conference if I click on this

now you can see that I have that nice

little article there and again same

thing play around with the prompt an

additional Ru if you want to further

customize the formatting of this

particular one there but if you're

satisfied then go go ahead and leave it

as it is okay great so medium is

done all right let me go back here so

now you can pretty much add all these

other uh posts the same exact method so

like for example you can just drag

another one for Twitter let's say right

search for Twitter X formally as Twitter

and you're going to create a direct

message same thing you're going to click

your connect to your account

unfortunately the thing about Twitter is

you have to have um a a basic or a pro

account in order for you to be able to

directly post via their API and that

limitation is because of X but if you

click on this open docs um naden has

really good step-by-step guide just

follow this step-by-step guide and it

will um it will make sense and things

will you'll be able to connect to your

account but basically you'll go to your

developer portal you'll create a

developer account right and right now as

you can see I already have one mine but

I don't have a basic or a pro so that's

why I can't like post this you will

click on the this gear icon right here

because if you don't already have an

project uh it will always have a default

project but you can always create the

other one and rename it and for

authentication you'll just come down

here and click on edit and then this

will um give you you you want to make

sure that you're copying pasting

callback URI and that is right here so

you want to make sure you're clicking

this and copying it and then you will go

to your developer app and just paste

this here website Ur URL you can just

put whatever you want I put my link in

there um um but then you also want to

make sure that you're selecting this

read and write and direct message

because you want to be able to do

everything from an8 end and you'll

pretty much save this and then that will

generate and give you a um client ID and

a client secret where then all you have

to do just copy and paste it here and

then your account will be connected but

since I already have mine like I said

I'll just get rid of this and now you

can just basically do the same thing

right grab your user once you're

connected and then you can grab the

Twitter post here and this will be um

this will post that message directly

there same thing with um Facebook so let

me go ahead and grab

Facebook Facebook has a trigger as well

but you're going to click on Facebook

Graph API and the same thing click on

the credentials here I didn't connect my

P Facebook but but it's pretty same

thing it's kind of like the simple uh

guide that they have here just go ahead

and create you'll create a new app put a

name in a contact email and then all you

have to is just go and create that app

and it'll give you a token that that you

could generate from there through the

app access token and then you'll come

back and just paste that in here and

you'll be good to go so then you can

again post um all of these things

together uh so another good thing is um

you can actually have a separate AI

agent that generates a summary article

for your internal teams or for yourself

so for example you can add an AI agent

here if I could type AI agent agent and

this time for example let's say I want

to use this a conversational agent let

me grab get rid of this you're going to

delete

this let's say I want to use a different

chat model right because I don't want to

use open a let's say I want to use

grock you can select um this whatever

whatever large language model you want

to select and now and prompt this model

to say hey you're going to Define below

you will just basically click on

expression

and you will type you will typee

summarize the former article to be sent

via email and slack let's say right so

then I can essentially grab the article

that's coming out of this and further

summarize it because we I can grab this

from my perplexity summary if I just

grab this to here right now I have this

article and now I can send this and ship

it off as another summary that could be

sent to email or slack and then I can

attach

this let me actually go ahead and do

that real quickly test

step there you go so now I got this uh

summary right here that was done via

groc so now I can attach a Gmail and

send myself a quick Gmail message about

this particular article send message

right connect to your account and you

can just basically grab this message

with an output or whatever right and

that will uh send that oh why is this oh

you can put your um email here and as

basically this will send you a nice

little summary email you can add a slack

message either here or from here

whatever uh it may be so let's say I

want to add a slack message of this

summary as well same thing

oops

slack boom you can send a message to a

particular group let's say send a

message now I can select my

credentials uh oh the input is coming

here so yeah that's why but anyways

that's fine we can send a message to

channel from list you can choose a

channel let's say I'm going to do AI

agents and let's for now let's just add

a test

here get out of this okay let me shut

this off because I didn't attach these

cuz this will give me an error otherwise

okay now so let's go ahead and um

execute this entire workflow so if I get

rid of this I click on test workflow now

everything should be able to work first

this is going to go ahead and generate a

LinkedIn article a medium article

obviously these two are deactivated

that's why it won't do that but it can

if you have this activated then it'll do

the same thing automate that process and

then it's going to uh come come down to

the AI agent here this is going to get

processed this is going to send me an

email and then obviously from there I'm

going to receive a slack message as

well there you go so LinkedIn got post

it's got an error uh let's see what's

going on here the service is receiving

too many requests from you oh okay yeah

just because I think there's a limit for

the AI and I I did too many different

API calls so that's probably why it's

not allowing but anyways for you it

shouldn't this this error won't exist

but as you can see everything went to

this proper Channel and then this one

same thing reason why it stopped is

because it um uh because of the error

here but here same thing everything went

through properly and now you should

receive an email uh if you put your

credential and everything as always I'm

going to uh paste this or provide this

template to my school community so all

you have to do is uh you can come in

here import from file and you'll be able

to go to the um classroom section here

and this will be under individual so I'm

going to post this video obviously in

this section right here but I'll also

have it under the NN templates uh with

the rest of the templates that I've

created where all you have to do is just

basically import it and you'll be able

to have access there where you can have

a reference so that way you can see that

if something comes up or if you run this

kind of errors and then obviously if you

have any questions uh feel free to post

it on the ask and assist channel in the

community and somebody or myself will be

able to help you all right well

hopefully you found this helpful let me

know if you have any questions like And

subscribe for more great upcoming

content I'll see you on the next one

he



so AI agents there's so much information

out there it can be overwhelming trying

to learn about them so I wanted to come

in here and break it down simply just

the way that I wish someone would have

explained it to me when I first started

learning about them I'm pretty new to

this space too and I've definitely felt

confused when trying to learn about some

of this stuff so hopefully you guys find

this informative and by the end you have

a good idea of what these agents are

capable of and how you can start

building them to make your life easier

and ultimately make a ton of money off

them I also plan to make videos about

this topic specifically tailored towards

people new to the space

so if it sounds like you and you want to

dive into the AI agent space or AI

automations in general definitely check

out some videos in the future but yeah

let's just hop right into this one so I

wanted to start off by touching on the

golden opportunity that I see and that a

lot of people are starting to see in um

the AI agent space so I was definitely a

little skeptical um about the hype and

you're completely saying to be

skeptical but check this out so this is

search interest in AI agents over the

past year as you can see it's

skyrocketed um right now is definitely

the best time to get in while sort of

like ride the wave you know as they say

while everything's new because

inevitably everyone will be in the space

and everyone will be making money off of

this so now is a golden opportunity to

learn and just sort of dive in that's

what I'm trying to do at least all right

so first things first what exactly are

AI agents simply put um an AI agent is

like having an employee who has Perfect

Memory follows exact instructions

doesn't sleep and costs a fraction of

hiring an actual human being they're

powered by Advanced AI models so they

basically have a brain and their brain

has Perfect Memory because it's going to

pull the information that you're giving

it whether that's you know information

about your company information about um

their client profile whatever it may be

they'll be able to recall it perfectly

which is so much better than the way you

or I can recall information that we read

in the past they're always going to

follow your EXA exact instructions so

whatever you prompt them to do is

exactly what they're going to do um a

lot of humans can sort of stray away

from that kind of stuff so that's huge

too they're never going to sleep so

they're going to be working 24/7 even if

it's something as simple as customer

support um and your clients won't have

to wait you know leave you a voicemail

wait for you'd respond to their emails

that kind of stuff they're going to get

um feedback right away or they're going

to get the answers they need right away

which is just huge for you know boosting

relationship and getting all the value

out of the customer that you're trying

to get um and then also like all of that

those are all just positive things those

are all pluses and it's just going to

cost a fraction of hiring an actual

human so um yeah it sounds too good to

be true almost um I've also seen agents

that are able to call up clients

potential clients um try to upsell them

try to book calls whatever it may be and

the client almost has no idea it's an

agent because it just it sounds so real

and they're able to have like an actual

conversation and um I've seen Tik Tok

and Instagram accounts that are 100% ran

by an agent um you know they create the

content they um push it out onto the

social media whatever it may be and they

they can do all this kind of stuff just

based on um the tools that you give it

and the way that you prompt your agent

to act so here's kind of what we did in

the past right we let's say it was we

wanted an agent to send an email for us

or we wanted to send an email

we would read the email we would put

that into chat and have it read it for

us and generate a response copy and

paste it over into Gmail and then we'

send it off ourselves so it's definitely

nice like a nice use of AI and chat gbt

but

um with agents like all of that's

removed pretty much it'll do that all of

that automatically for you so how

exactly do AI agents work so AI agents

are powered by a large language model

that's sort of their brain um and that's

just something like chat gbt or claw and

because they have a brain they can make

decisions they can handle Dynamic tasks

and they can adapt to new information in

real time and what makes them even more

powerful is that they're not just

limited to one action or task you can

give them multiple tools um access to

your calendar CRM whatever it may be and

they'll be able to combine those with

different logic in order to do the job

that you want it to do so here's just a

quick visualization um on the left we

have an entity this is a human um human

as a brain they can reason they can use

logic to make decisions and then you

give the human access to tools like

Excel LinkedIn Google word slack Google

Drive whatever it may be so just think

about it as simple as that right The

Entity is just an AI agent with the

ability to reason use logic to make

decisions and access the tools that you

give them in order to do exactly what it

is that you're prompting them to do so

no need to over complicate it like I

said

this is all it really

is um okay so I wanted to touch on sort

of the difference between traditional

automations and AI automations so here's

just sort of like a flowchart logic you

may call it of a process so it starts

you go through a couple things um and

eventually you get to a point right here

where you need to make a decision and so

this is where um you know I work in

automation

so when you're when you're trying to

automate processes there's a lot of

things where it's going to be like a yes

or no or it's going to be is a number

higher than 10 or lower than 10 um a lot

of stuff is going to be a clear you know

black and white answer and that's where

automations break if it needs to be

dynamic or if there's any sort of

reasoning that needs to go into it any

sort of thinking that needs to go into

it that's when they get tough to

automate because you you think oh I need

a human to be able to think through this

and make that decision but with AI

agents they're going to be able to do

that because they have the brain of a

large language model so we all know that

chat's really good at um writing a

discussion post for you maybe if um you

taking a college class or um reading an

article and then giving you a nice

summary because they have the ability to

think and use background information and

adapt to sort of like what is being

thrown at them so just super super cool

stuff

here all right so moving on to why you

should care about agents and why you

should care about this opportunity so

the first thing is efficiency and cost

savings obviously agents are going to

save you a ton of time and money they're

going to give you the same leverage as

hiring employees but without the cost of

salaries benefits or training all that

tedious stuff next we've got scalability

they can scale super easily if you need

more agents um just make them just build

them if your business is growing you

don't need to hire more employees that

can if the work can be done by agents so

they can handle the increasing workload

without breaking a sweat um they're not

rigid traditional automations so they're

not going to break when things

change um the next point it's a great

segue into adaptability um they're able

to like I said it's very dynamic they

can adjust their behavior based on new

data changing environments unexpected

scenarios um it all kind of relates back

to the way you prompt an agent I won't

get too much into the prompting of an

agent right now but the more examples

you give it it's sees like what is

coming in and how to react um it'll be

smarter and smarter and as you sort of

interact with it more it'll it'll get

smarter and

smarter next we've got the ability to

make decisions we talked about this with

traditional automation but they can

analyze data they can reason they can

choose the best course of action um

which is perfect for complex tasks that

you couldn't achieve with traditional

Automation in the past fifth we've got

the ability to build them so easily a

lot of people probably think that you

need to have majored in computer science

and know how to code in Python Java all

that kind of stuff but you really don't

um nowadays there's so many low code no

code tools out there to be able to build

agents there's so many good tutorials on

YouTube on how to build agents whether

it's um relevance AI super intuitive

make zappier um something like n8n is

something that I've been using recently

to build agents um super super easy to

learn and this is a great time to learn

because like I said earlier evitably

everyone will be learning so get ahead

of the curve to the point where you can

be able to teach people how to do it and

then sixth last but not least we've got

the future it's just a super super

exciting time to be in this space these

agents are constantly improving um in

the future businesses May no longer rely

on large teams for everyday tasks and

I'm not saying that humans will

completely be removed out of the process

like I don't really think that's super

realistic but just like freeing up that

time for humans to do higher impact work

is um definitely definitely super

important

and yeah pretty

much all of these reasons is like do I

even need a seventh that's that makes me

want to build agents I don't know about

you guys but so where can you use agents

um I'm not really going to get too deep

into this in this video because that

could be like a 30- minute topic there

there's so many places where I see these

agents being able to be implemented but

we'll just cover sort of four main

points right now um

four big areas of a business where

agents can be utilized is um we've got

marketing we've got onboarding customer

success and project management that's

just like the four that I'll briefly hit

on today so first one we said was

marketing stuff like cold Outreach um

this has been able to be automated in

the past but not as personalized as

these can be because these agents can

get background information on whoever it

is that the email is going to and they

can really personalize it to the to the

point where the prospect has no idea it

was written by basically a robot um

scraping leads qualifying leads same

thing with follow-ups they can be

personalized really well and content

creation um like I said about those Tik

Tok accounts that are completely run by

AI it's um it's

insane next we've got onboarding there

are a lot of you know things in place

when you bring on a new client that you

have to do a lot of documents you got to

collect a lot of information um you want

to make them feel like part of a

business and a lot of this stuff can be

automated with AI agents you got

customer success um this is just stuff

like getting feedback from your your

clients um making sure they're happy

making sure that they're not always

leaving you voicemails um an agent can

sort of handle that kind of stuff really

well because it has all the knowledge

that um you're giving it as far as

information about your company so then

next we got project management we've got

stuff like agents can schedule meetings

they can upload documents um Track

Performance this kind of stuff um even

if it's just a very small part of a

larger workflow just being able to save

5 minutes a day here and there

definitely add up especially with um you

know small businesses so yeah that is

pretty much all I've got um hopefully

that gave you guys all some high level

insight as to what agents are what they

can do um I also hope that this piqu

your interest in and made you sort of

want to play around with building some

and implementing them into your business

or your life in some way

um like I said I really think this is

the way that all businesses whether

they're big or small are going to start

to move um to conduct some of their

operations in the future so this is

absolutely the perfect time to start

learning from or learning about this

kind of stuff but yeah like I said I

plan to continue making videos on this

topic tailored towards beginners in this

space um tutorials more insights into

how they can be used how they work so if

you're interested in that kind of stuff

definitely check out some videos in the

future but that's all I've got for today

so thank thanks guys




all right today we've got a very

exciting one this is the nadn master

class where ideally I'm taking you from

a beginner in nadn all the way to an AI

agent Builder by the end of this or even

just someone who wants to implement AI

automations into their daily life or

into their work so I was about to say

grab a pen and a piece of paper but more

realistically since you're here grab

some sort of AI notetaker and let's dive

into this one this is a master class so

we're going to start at the bottom start

with the basics and we'll continuously

work our way up but just want to start

off here with what is any

so at this point I'm sure you guys have

been hearing the term low code no code

tools and nadn is a low code no code

automation tool so that just basically

means that nadn allows users to automate

processes build workflows with minimal

coding knowledge and the key idea behind

this is that low code means it's very

easy to develop things with a very

userfriendly interface where people can

just go in there and drag and drop

different components different nodes is

what they're called in nadn to create

these flows without having to come in

here and type a bunch of JavaScript or

python this is so significant because

it's going to allow anyone to be able to

get an in and get up and running with

building automations even if you don't

have you know a background in computer

science or programming the barrier entry

to this is so low it's very very

accessible for anyone to get in here and

start playing around with stuff but even

though it's very simple it also retains

a lot of flexibility for more advanced

users who do have coding background and

they're able to come in here and take

some of the basic principles and also

come come on top of that with you know

custom code or different type of logic

and Integrations and it's a very very

powerful tool you can build tools

directly in NAD as you see here and

that's a little bit different from other

things like make or zappier because you

can build let's say an agent that's able

to call four or five tools and these

tools you built within NN itself which

is just super super cool stuff what

about the importance of automating workf

flows so we've got five points here I'll

touch on real quick increasing

efficiency and productivity automation

is going to eliminate repetitive tasks

it's going to reduce human error and

it's going to allow you and your team to

focus on higher value work it's also

going to save time and money of course

automating workflows is going to reduce

operational risk free up Time by

completing tasks faster than manual

scalability and adaptability you can

scale a lot more effortlessly you can

focus on your growth as a business and

these Solutions these automation

Solutions can be customized or adjusted

to meet your changing needs you've also

got improved data handling automation is

going to integrate data from various

sources it's going to provide real-time

insights for better decision making and

then the last benefit I wanted to hit on

here was enhanced customer experience

you're going to be able to respond

faster to your clients or automatically

to your clients personalize interactions

through automated workflows and all of

this is just going to lead to better

customer satisfaction and Customer

Loyalty moving on here we've got why

should you learn nadn so when I was

building the slide I had so many

thoughts and I tried to put them all

under three main bullets and so this

first first one here is nadn empowers

non-developers with Automation and I

know we've touched on this a little bit

with the whole low code no code stuff

but it's just so powerful that anyone

can pretty much come into NN and start

building things in 15 20 minutes that's

actually going to automate real work

that they would do on a daily basis so

even if you're not a programmer you can

come in here create workflows it's going

to save you time make your life easier

for example you could very easily get up

a workflow that is going to

automatically move data from one app to

another like ually copying contacts from

one spreadsheet to another without

having to do it every time it's like

having a digital assistant that can

handle these repetitive tasks for you

and you don't really need the technical

skills to set it up so super cool stuff

the second one we've got access to over

300 built-in Integrations which is

insane andn comes with a ton of

Integrations ton of connections to

popular tools that you probably use

every day like Gmail um Google Sheets

slack Twitter we got Microsoft stuff too

if you want to connect to teams or

Outlook it's super super cool what you

can do these Integrations let you

connect quickly to these tools and you

can connect tools to other tools without

needing to like code in between that for

example you could set up a workflow

where every time you receive an email

it's going to automatically add that

information to some sort of spreadsheet

and then it's going to send you a

notification on slack or teams and all

of that will take place without you

needing to be in there and doing it

manually then this last one you can

connect to almost any tool so kind of

similar to the second point but if

there's something that you want want to

connect to that there's not a built-in

integration to you can still pretty much

connect to it whether that's through an

API or a web hook um these ones are a

little more technical but for the most

part um you know a quick YouTube video

or using chat gbt even you'll be able to

get them up and running and connect to

almost anything you want a little bit of

custom code and um really when you

realize you can connect to almost

anything then you have almost endless

possibilities of what you want to

automate all right we're going to be

moving into part one of this master

class here which is just very simple

getting started with NN we're going to

talk about how you set it up the

different ways you can set it up and

then we'll just get into the interface

and start actually learning what it

looks like and what everything does the

first thing I think that we should talk

about when it comes to setting up your

NN is if you want to set it up

self-hosted or if you want to Cloud host

and I'm going to run through a few

features of each of these two different

options and then we'll talk about which

one you should choose so first with

self-hosted some of the things that it's

going to offer you are control and

flexibility you're going to have full

control over your environment you can

customize your server integrate with any

internal system you have the ability to

adjust your configurations as needed

we've got data ownership so all the data

and workflows are going to stay on your

private server so this is ideal if you

need to comply with privacy regulations

or you want to keep sensitive data

in-house cost self-hosting can be more

cost effective in the long run it

depends on the server and maintenance

costs but there's no ongoing

subscription fee to naden like if you

were to do Cloud hosted but with the

cost as aspect you may need to account

for infrastructure with like database

management or server hosting and you

also may need to have some sort of team

that will help you maintain it but who

knows fourth with self-hosting is

installation and maintenance you are

going to be responsible for setting up

and managing and updating your instance

this also includes backups and scaling

so this is going to require more

technical knowledge then finally we've

got customization so you can modify the

source code you can add custom features

that might not be available in the cloud

environment so this is cool if you want

complete freedom to modify the system as

you want and now moving on to the cloud

environment here are some features of

cloud it's going to be easier to use

because it's managed by nadn itself so

there's no need to worry about setup

updates scaling maintenance stuff like

that so good for beginners you've also

got availability and reliability so the

NN cloud is hosted on a scalable and

reliable infrastructure it's going to be

maintained by Ann's team so they're

always going to keep stuff up to date

with the latest features and Bug fixes

the security is a little different it's

going to be managed security so SSL

certificates or you know secure API

handling and that's going to be done by

the N team and then also this is going

to be more suitable for users who don't

want to handle server security now when

it comes to cost of nadn it's really not

that bad either way the cloud version

comes with a subscription model that's

going to be based on usage tiers how

many products you want how many seats

you want on your you know an inn

environment and so you'll be basically

paying based on that so in the long run

it could be more expensive if you have a

ton of users and a ton of projects going

on but if that's the case then hopefully

you're either saving a ton of money or

you're making a ton of money so balance

is out then finally we have data

handling different than self-hosted data

is going to be stored and processed in

the cloud so like I said if you're a

business dealing with highly sensitive

data this may be a limitation due to the

server dependencies okay so at this

point you may already have an idea of

which one you're going to choose but if

you don't real quick you should go with

self-hosted if you need full control

over your data and your infrastructure

if you want to integrate any in deeply

with other on premise systems and if

you're technically comfortable handling

server maintenance and management or you

have a dedicated team that will do that

for you and then you're going to want to

go with Cloud if you prefer Simplicity

and you don't want to handle

infrastructure or server maintenance you

want a quick setup and reliable hosting

it's going to be managed by the NN team

and you're okay with paying for a

subscription for a managed service and

you don't mind being handled by a third

party provider okay so before we

actually hop into NN and we look around

at the interface probably important to

understand the difference between

workflows nodes and executions so I'm

going to break this down as simple as I

can pretend you're in a restaurant we've

got workflows which are going to be the

recipes nodes are going to be the

ingredients the steps within each recipe

and then executions are going to be

every time someone sits down and orders

that specific recipe or workflow so the

workflow think of it as like a set of

instructions that you're going to be

giving to nadn in order to automate a

task so for this example we'll say that

the workflow is a a chocolate cake then

we'll move down to nodes nodes are like

the building blocks of the workflow each

node is going to represent a single step

a single action within a workflow so one

node might send an email one might

update a spreadsheet one might pull data

and then you can kind of Link those

together in order to make the chocolate

cake so you know eggs flour baking soda

we're going to put those together then

we have the execution which is simply

just running your workflow in nadn this

can happen by different triggers whether

you want to do that manually or whether

you want the automation to take place

every time you update a row in a

spreadsheet but in the example like I

said just picture someone coming to the

restaurant and ordering a piece of

chocolate cake and then you kind of

start that process of making the cake

and delivering the cake all right now

that we've covered the three main

building blocks that go into pretty much

every automation let's actually get into

nadn look around a little bit at the

user interface see what I'm talking

about when I say drag and drop we'll

talk about accessing Community Resources

Community templates stuff like that and

it'll really start to make more sense

all right so we're in nadn as you can

see as what we're looking at right now

is we're just on my homepage so it's

going to show me a ton of the different

workflows that I've been working on um

we've got our projects right here so I

only have the one right now it's called

Nate testing so in here it's pretty much

just everything I have but if you had a

specific project for a specific client

or a specific project for an actual

specific project at work you could add

them here so you can keep everything

organized honestly my stuff is not too

organized but here's what it looks like

we've got stuff on the Le hand side we

can see we have an admin panel we have

templates we have variables we can see

executions of each workflow we've got

some help and then you have your profile

down here as long as well as you know

I'm Cloud hosted so I can see that

there's some updates here with some bug

fixes that I'll I'm going to be able to

just go in and install real quick let's

just add a new workflow right here and

see what the interface sort of looks

like so this is the canvas that I was

talking about where I said it was a very

userfriendly drag and drop interface the

first thing you're going to see is that

you have and add First Step button so

we'll get into different types of nodes

after this and we'll talk about triggers

and all that but first step is always

going to be a trigger so you'll click on

that and it will list up you know some

triggers trigger manually just means

that you'll be hitting test workflow

button down here in order to run the

workflow execute the workflow every

single time you can schedule it you can

do um on chat message you can call it by

another workflow so that's where all the

stuff is super powerful we'll just add a

manual one so you guys can see what it

looks like this is where you hit test

workflow in order to run it and you know

obviously nothing's coming through but

it didn't fail so that's good then from

here you would want to add different

nodes to connect to so you could do that

from either clicking on this plus button

where it says click to add node or drag

to connect or up in the top right you

can click up here and it will pull up

this panel for you to search through

nodes you know by category or you can

just search for them if you want um

another cool thing with the triggers is

there's not just those triggers there's

different triggers for each app so let's

say that you wanted to run a workflow

every time you got an email you can

click on on Gmail down at the bottom

you'd see different triggers and this

one says on message received so this

would execute the workflow every time

you get an email and you can tell a

trigger if it has this little lightning

bolt so that's a trigger node but

anyways let's just say that we wanted to

put some fake data in here so I would

just come in here and I could either

type for the the node that I want or I

know I'm looking for an edit Fields node

so I can come to data transformation and

I would see edit Fields right here this

is where I could configure stuff so let

me just quickly pretend um we're going

to make make a field called name and

we'll just put in my name and what's

really cool about NN is that you can

test each step individually as you're

going through and automating something

so rather than having to run the whole

workflow you could just test step right

here we'll see that what's coming out of

this node is Nate um in the field called

name so we have that information running

through but it's nice to know because

you'll always see on the left of this

configuration panel you'll see data

that's coming in and then you'll see

data that's coming out so it makes it

really easy to troubleshoot and test

each step individually which is really

cool

but you have to make sure that your your

um nodes are connected because let's say

you know I didn't drag this one right

here and connect it to the edit Fields

if I was to run

this nothing would come through the edit

Fields there's no output as you can see

it says wire me up this node can only

receive input data if you connect it to

another node and yeah so that's how

that's going to work I say this is

probably all we'll do for now in here

we'll get into some Community templates

and just show you how that all works but

as far as just basic setting up a

workflow and seeing what um the

interface looks like how easy it is to

just drag and drop stuff that's what

we've got so back in the homepage we've

got workflows you all can also look at

your credentials so this is just

different things that you've connected

to like I said there's so many

Integrations so it can easily access my

Google Drive my telegram my Google

Sheets all that kind of stuff so that's

where you can sort of see and manage

your credentials and then down here the

only thing I'll touch on real quick will

be the templates you can click into

templates and it will pull up nad's

website where there's sort of like this

community where people can upload cool

things they're building

or you can search for specific use cases

specific um you know tools that you want

to use so it's a really great place to

get in here and learn but as you can see

we have you know learn by doing so you

can download these templates which is

really cool sometimes it's you know it's

nice to watch a tutorial on YouTube but

being able to really learn you have to

just get in there and you have to let

things fail in order to figure out why

they're failing so right here we have

you know AI agent chat we can download

from NN we can click here we can look at

it um and we can see what's going on we

could click this button here to download

it and um start playing around with it

in our own nadn we have this one where

you can click in here and a lot of times

people will annotate like what's going

on so you can see how to set it up you

can see which you know what's taking

place in each scenario so that's super

super useful and then I'll just show you

real quick let say you wanted to use

this one we could just import the

template to my cloud

environment and as that loads up it's

pretty much just going to put it right

into my workspace so I've got this

information here I can now test this

data I can look at what's going through

each step we can see right here we've

got um you know this information's

coming through and then it comes out as

you know flour eggs milk which is

interesting because I just did a you

know a little example about cake so um

seems like it's meant to be but either

way you can start to see actual data

moving through which is how you're

really going to be able to wrap your

head around what's going on another

great thing about nnn is there's so much

documentation it's super easy to get

help so if you come down here you can

see help we've got a lot of stuff here

they even have a course that you can go

through through but documentation if you

click on here you can see pretty much

anything you need to find like there

there's quick starts there is um

Concepts about flow logic Concepts about

data so like I said super easy to learn

about all this kind of stuff you can

look at you know what each node is doing

specifically so let's say you were

confused about the loop node you could

come in here read about

looping you could see you know how the

node works you could maybe see some

examples of how people are using it and

yeah like at the bottom it's probably

going to throw you in some you know

templates of actual workflows with loops

but super easy to get help Within naden

part two of the master class we're going

to be talking about some Core Concepts

so we just saw what the interface looked

like we saw a few nodes but now we

actually need to dive into different

types of nodes and what they do and then

we're going to end this section of the

master class with an actual example

where we'll get into nadn I'll do a live

build of a really quick Automation and

then we'll talk about the different type

of nodes and how data is moving through

so it should be pretty cool to see so

before we in nadn and we build out our

first automation we really need to

understand these sort of four main types

of nodes so we've got Trigger action

data transformation and logic so let's

just break these down real quick

starting off here with trigger nodes

because a trigger node is pretty much

going to be what starts every workflow

we just saw these in nadn they were the

ones with the little lightning bolt next

to them anyways different types of

trigger nodes we can look at something

like a web hook trigger um an email

trigger like I showed you anything

that's going to start the the workflow

whether that's going to be manual or on

a chat or on an event or I have called

by another workflow bolded here because

it's sort of the power of NN you can

build a workflow that will be called by

another workflow and then you can build

an agent that can call that workflow as

well as maybe this agent can call like

10 other workflows so super powerful

stuff here next we've got action nodes

these are the actual doers they're going

to perform a very specific task within

your workflow so it's like an assembly

line this guy is going to to um you know

put the present in the Box this guy's

going to wrap the present this guy's

going to put the bow on the present all

that sort of stuff but they can do

different things like you know send

email create a record make an API

request they can get a text message they

can set your calendar um almost anything

that you could do on your computer on

your phone manually you could have some

sort of action node to do this thing

third we have data transformation nodes

these are going to help you change or

process your data in some way so that it

flows through the whole process and you

get the end result as you want want it

so these type of nodes can do things

like set that can add Fields change

values within Fields it can do some sort

of processing your data you've got

something like an aggregate where you

can combine a ton of data into a single

output or something like a merge where

you can combine data from two different

sources and put them into one the last

type I'm going to touch on real quick

are logic nodes these are sort of the

decision makers they're going to help n

and figure out what path to take how to

handle a different situation so we've

got something like an if node it's going

to check if a specific condition is true

or false is you know this value higher

than 10 it's going to go this way

otherwise it's going to go this way

we've got a switch node which is going

to allow you to put multiple conditions

in there and it's going to be checked

and direct the workflow to a specific

action based on that conditional check

and then something like a weit node

which is going to pause the workflow

let's say you wanted to pause the

workflow until you come back and respond

like yes that's good to go then it will

continue to move on through the rest of

the process or you could have it like

wait for 20 seconds um what whatever you

want it to do all right now it's time to

finally hop back into NAD in hopefully

these slides weren't too boring but

we're going to be building an example

workflow here it's going to be really

simple it's just going to automatically

process customer orders and then it's

going to summarize it and send us a

report automatically every time we get a

new order so super cool stuff let's hop

into how we're going to build this thing

all right we are in a Google sheet this

is going to be the customer order data

that we'll be using for this example so

I had chat gbt make up some data for us

we've got stuff like order ID customer

name product quantity price order date

and the status of that order so every

time a new row is put into this Google

sheet it's going to run through nadn

automatically it's going to get

summarized by some sort of large

language model like chat gbt or Claude

and then that summarization is going to

be emailed off back to us or back to our

team automatically so this will be a

nice simple example but it's going to

feature different types of nodes and

we'll be able to see the data move

through real time so it'll give us a

really good base we are now in n8n this

is the canvas we'll be working on and

this is the workflow that we'll be

building here um NN masterclass customer

orders so we know the first step that we

always need to do is add some sort of

trigger we'll click in here and we can

see different triggers like manual um on

app event called by another workflow we

talked about this but in this case we

want to make this one automatic so we're

going to be doing a Google Sheets

trigger Google Sheets has three triggers

it's got on row added on row updated or

on row added or updated so we'll do this

one because that way if you have to go

in there and change some sort of

information about an order like let's

say one goes from you know the status is

pending to shipped or something we'll

also get an email about that so we have

to set up the Google Sheets account um

this is where you're going to have to

set up a credential and I'll walk you

guys through how to do this so you're

going to click create new credential and

you'll see this screen pop up where we

need to grab a client ID and a client

secret um this looks a little confusing

and I was definitely confused when I

first saw the screen so what we need to

do is right here um I talked about how

nadn has is really good at having

documentation that explains stuff so

we'll click on open docs right here we

will see that the prerequisite we need

is a Google Cloud account so we'll go in

here and make a Google Cloud account um

and then we can see that it's going to

walk you through step by step so if my

explanation isn't good enough you can

come in here and grab the docs but

hopefully I'll show you real quick how

to do this so we'll come into Google

Cloud um this is what it's going to look

like you'll have to sign in make an

account then you want to go to your

console once you're in your console

you'll see the screen

you might not know what to look at but

all we want to do is we're going to

create a project so mine right here is

just called my first project make sure

you're in your project and then you want

to come in this left hand side to apis

and services we're going to click on

enabled apis and services and at this

point you just need to search for a

Google Sheets so we're going to type in

Google um okay we need to do sheets be

more specific so Google Sheets we can

see Google Sheets API we'll click in

here and then all you need to do is just

enable this API so we've got ours

enabled already

um there will be a button right here

it's just as simple as that so get that

enabled and then you're going to come in

here go back to your apis and services

and then we want to go to

credentials once we're in credentials um

this is where you can set up your client

IDs to get an ID and a secret so I'll

just walk you guys through how we're

going to do this one you're going to

click create credentials up here you'll

go to ooth client

ID once that loads up you want to choose

the application type this is going to be

a web app you can name it whatever you

want we'll call this one demo for for

the sake of this video and then all you

need to do here is add a redirect URI so

this is where you see in nadn you've got

this UD redirect URL um we're just going

to click here to copy go back into

Google cloud and we're going to add this

right in here just just paste it in and

then you'll hit create you'll get the

screen pop up with um your client ID and

your client secret so it's as simple as

copying the ID pasting that into the ID

field in NN going back to Cloud grabbing

your secret and pasting it into the

secret then you want to sign in with

Google so this screen's going to pop up

it's just going to be a simple prompt to

sign in with Google like you would

normally have um so I'll drag this in

right here and now it says that Google

hasn't verified this app so this is

where you need to set up your ooth

consent screen um so back in here you've

got your ID and your secret now you need

to go back in your credentials right

here ooth consent screen all you need to

do here is either make sure that your

app is published so um you need to make

make sure the app is published so that

it has you know access to actually go

through and grab information out of your

Google Sheets your drive your email

whatever it is or you can add yourself

as a test user so I've got my emails

down here as test users this also will

allow these emails to sign in and go

through but if you're getting blocked

for some reason it's probably because

you didn't set this up right so just

make sure it's published or that you're

in there as a test

user so back into nadn um we've got this

signin field we'll hit continue just

make sure you give this email access to

everything give NAD access and then

you'll hit continue and then pretty much

you'll be good to go you'll see we got

this account created right here it's

green we're good so we will come out and

now we're

connected so now that we're connected we

can configure the rest of this node it's

going to be running every minute and

that's when it's going to be checking

for if a row was added or updated now we

can select the document that we want so

it's really nice you can choose from a

list you can enter the URL or the ID of

your document but list is so much easier

it's just going to access your Google

Drive and see what sheets you've got so

we're going to do customer orders um

there's only one sheet in this document

so we'll grab that sheet and it's going

to trigger on row added or updated so if

we can fetch a test event here we'll see

some of our sample data coming through

so as you can see we've got um five

items we've got the columns up here and

then we have all of these orders that we

just had right here in Google Sheets so

we've got John Jane Mike Emily Robert

Brown and in here you can see we've got

John Jane Mike Emily and Robert Brown so

this node's working we've got our

information coming through into NN now

we want to add an open AI node so we'll

just click on this plus right here or

click on the plus up in this top right

corner and you can search for a new node

we're going to grab open AI you could

use a different large language model if

you wanted to but I'm going to be using

open AI you can see we've got 15

different actions within this node what

we want to do here is message a model

basically just means that we're going to

be talking to chat GPT just call this no

summarize and now we need to hook up

this node with our credentials so at

this point if you don't have an open AI

account you need to do so and then once

you do that you can come in here click

create new credential this time all we

need is a single API key so once you

have your open AI account you'll come

into it on left hand side you'll see all

the stuff but we just want to go to API

Keys up in the top right you can click

create new key give it a name and then

it will give you a value to copy so

pretty simple same thing you just want

to come in here and copy that

information in or sorry past that

information in hit save and it will go

green once you're all good um so that is

all you got to do but pretty much every

time that you need to configure a node

you're going to have to grab some sort

of key so just keep that in mind so as

you can see the resource is text the

operation is messaging a model and now

we need to choose what model we want to

message so I'm going to come in here and

grab GPT 40 right there and now we need

to configure the rest of this node so

this is the message that we're sending

to GPT 40 you have a couple options here

you can have it be a user message an

assistant message or system message you

can see the differen is right here

usually when you're going to be

prompting the node how to act we're

going to choose system so in here I'm

going to type a quick prompt and I'll be

right back to explain it all right here

is the system prompt that I came up with

just typed this out really quick so I

said you are in charge of client orders

your job is to take incoming information

regarding new orders and give a nice

summary that will be emailed to the team

the email should be signed off from

customer success team and then we want

to give it the information from the

previous Google Sheets trigger that's

coming in here on the left we need to

actually give it the information to

summarize so it's going to be getting

order ID customer name product quantity

price order date and status and so all

we need to do is come in here and drag

and drop each of the

fields into the prompt and it will be a

variable so it will change for each one

so I'll just show you guys order ID we

drag this in and I don't know why it

does that um we want to make sure that

right here with order ID so first of all

first thing to note this is a green

variable with the two curly brackets

around it that just means that it's a

JavaScript variable so this doesn't

involve any coding it's as simple as

dragging and dropping but this just

means that it's going to change based on

whatever value is in this field so as

you can see in the result tab right here

we've got the the json. order ID is

coming through as 101 because that's the

first order and you can see similar

things when we drag in customer name

we'll get in the the results we got John

Doe um we'll drag in everything else and

then I'll show you guys so we're just

going to drag in product quantity price

order date and Status so that's assigned

wherever it needs to be and then as you

can see in the result we've got here's

the information on client orders we've

got the correct order ID name price

quantity all this kind of stuff we have

the actual information coming through as

you can see and then the last thing that

we wanted to say was please output the

following parameters So based on this

information that it's getting right here

that it's going to sum summarize it's

going to Output an email subject for us

and an email body for us so we can go

ahead here and hit test step and I'll

show you one thing about how we want to

Output this content as Json so I didn't

check this yet and so that means that

this is going to execute and it's going

to all come out in one sort of like

large string so as you can see we've got

um for the first order email subject new

order confirmation order ID 101 here

actually let me make this a little

bigger so it says hello team we have a

new order that has been successfully

processed and shipped below are the

details so it's going to summarize out

for us and then it signs off thank you

for your attention best regards customer

success team but this is coming through

as one big chunk of text called content

so what we want to do is output the

content as Json we'll test the step

again and now it's going to come through

as two separate Fields one will be the

email subject and then one will be the

email body and this is just important so

that we can drag and drop the next

Fields later when we want to configure

the actual Gmail node so as you can see

right here we've got the subject and

then we've got the body and we've got

the subject and the body we'll read one

more real quick so order 103 we've got

the subject and then the body says we

have a new order summary order ID 103

Mike Johnson you got headphones at $200

just one pair please let us know if you

need further details so as you can see

these are all coming through as an email

subject and an email body and this will

be important when we set up this next

node here which is going to be a Gmail

node this time we're going to add the

node by clicking the plus up here it's

the same thing as this plus but just

wanted to show you guys different ways

we're going to grab a Gmail node and

there's 25 actions within Gmail as you

can see there's a lot of stuff you can

do which is just awesome but here we're

going to be sending a message so we'll

click on send a

message um real quick let's just make

sure we wire this one up otherwise it's

not going to work and then we'll come

back into the node and we can configure

it so first thing you got to do is

obviously set up your new credential

you'll come in here just got to grab

that same client ID and secret from the

previous one so we'll come back into um

our enabled apis and services

you want to go to

credentials and then you can click into

that um client ID that we just made and

then all you got to do once again is

copy and paste that information in so

let me just do this real quick we'll

grab the

secret paste that in there and then once

again just sign in with

Gmail it's again going to make you

verify the app we'll go through give

access to everything and then we go

green because we're good to go so we've

got that set up now all we need to do is

configure the rest of this node so as

you can see the resource is a message

the operation is that we're sending a

message now you can see why it's so

important that we set up the email

subject and the email body as two

separate Fields because we output it as

Json so all we got to do is drag in this

subject right here where it says subject

so the subject of this Gmail being sent

off will be order confirmation 101 for

John Doe and then same thing with body

you're going to grab that and put that

in the message field where this is the

actual message that's going to be sent

in the email we we want to make the

email type is text that's just how I

usually like to do it and then for the

sake of this example we will just put in

my email so we can see this email coming

through and you could make this variable

you could make this change based on the

order if you wanted to but right now

let's keep it simple we're just going to

send it to nerk 88@gmail.com every time

and finally you've got some options here

you could attach things you could CC

people you could change the sender name

variably whatever you want to do here I

usually just will come in here and click

append and add an attribution and make

sure I turn that off otherwise at the

bottom of the email it'll just say this

email was generated by nadn or sent by

nadn so this looks good to go we can

test this step and it will it should be

firing off five emails because we have

five emails um in the sample data so you

can see these came through it's just

giving us a message ID and a thread ID

which right now we don't need but you

can see that all of these got sent so

let's hop over to the email I will

refresh and we should see five new

emails in my inbox so yeah we've got

order um 101 102 103 104 and 105 so this

is information from all the orders as

you can see this one says new order from

Robert Brown he got a tablet three of

them actually 600 per unit so the total

price was 1,800 it was on August 28th

and the status is still pending so thank

you best regards customer success team

so all that came through exactly how we

wanted it so that's good to

see now we're back in n8n and we're

pretty much done with this workflow

we've got three nodes in here and we can

save it and now what we want to do is

check this box to inactive or sorry to

active so all this means is that now

that the workflow is activated it will

regularly check Google Sheets for events

and then it will trigger executions each

time that um a row is added or

updated and they won't show immediately

in the editor so that means like we

won't be seeing like these turn green

every time it actually is going through

but they will'll be going through so

let's hop into the Google Sheets real

quick add a new row and then let's let's

wait for the email okay so I've got this

information I'm about to paste into here

we've got order 106 for Phil dumpy he

ordered 500 crayons $5 for each one

we've got the date and we got the status

so now we're just going to hop into our

email and I'll just refresh and we

should see the new email coming

through okay so I just refreshed and we

can see this new New Order we've

received the New Order from Phil dumpy

here are the details 106 Phil dumpy 500

crayons $5 per unit we've got the date

and then we have the status so um as you

can see the date is actually coming

through is January 20

2025 um and we did not put January 2025

so what you can do here is because

there's you know a discrepancy we will

go back and N ITN we will go to our

executions over here or right here so

executions we can see this is the most

recent execution we'll click into here

and we can see what's actually taking

place

so as you can see the trigger went off

it grabbed one new item we'll open up

this message and model node so we can

see the information coming through and

you can see the date come through here

as

45585 so that's not what we want um

that's why it's coming through as um

January 20 2025 so what we need to do is

come in here and fix this specific node

because we see exactly where the issue

is happening I think the issue here was

just weird formatting with numbers

coming through as far as dates so let's

just try this one again I just out of

this row so it should be working right

now to fire off this email to us but we

kept this one as just plain text so

hopefully it reads through an n and end

as plain text but let's take a look at

the email and then we'll take a look at

the actual execution okay just refreshed

got this new order it's coming through

order 106 and we got the date correctly

as October 20th 2024 which is what we

put right here so let's go back into Ed

and let's refresh this page so we can

get the most recent execution and making

sure all the data is coming through

exactly how we want it and it's a great

thing to keep in mind that you're able

to go into the executions you can see

exactly how stuff's coming through so

from the Google Sheets trigger we're

getting this information and the date's

now coming through correctly how we want

it previously it was coming through as

just like 4554 whatever sometimes in

sheets it can be weird with date

formatting and then it's being able to

come through correctly order date and

it's giving us a nice summarization

right here we've received New Order with

the following details order ID 106 for

Phil dumpy crayons 500 all this kind of

stuff and then it's just going to take

that subject and and um body and put it

into a Gmail node which is being sent

over to Nate herk 88@gmail.com

which is what we see right here so that

was it for this first example I know it

was very simple we just utilized three

nodes to build this workflow that

automatically takes data every time a

row is added in your Google Sheets it's

going to summarize it with a large

language model of chat gbt 40 and then

it's going to move into the Gmail node

which actually sends it off and this was

one execution of this work worklow okay

now we're moving into part three of this

master class which is going to be

talking about Rag and Vector databases

I'm sure you've heard these terms but

maybe you don't completely understand

them so I'm here to break it down for

you and then we're going to end this

part with going back into nadn building

out a simple rag AI agent and this will

include you know actually uploading

information into a vector database and

then being able to use an agent and rag

in order to go talk to that PDF or file

and get answers back okay so what is is

rag rag stands for retrieval augmented

generation and it's a very powerful

technique that's going to combine two

different approaches the first part is

retrieval and then the second part is

Generation so this technique really

helps AI models provide accurate and

relevant answers especially when you

need upto-date or specialized

information so the first part here is

retrieval when you ask the AI a question

instead of it making up answers based on

its training data it's going to retrieve

relevant information from um external

sources so in this case the pine cone

Vector database that we're going to be

setting up um so this is obviously going

to be the database but it could be other

documents or it could be websites and

then the generation aspect of it is

after it retrieves back this information

that's relevant and accurate and up to

date then the AI model will use this

information to generate an answer so

this is where the AI actually crafts a

human readable response with the

information if you don't already

understand from that previous slide why

rag matters let's break it down real

quick let's say for this example you're

using an AI assistant that needs to

answer questions about your company's

internal policies you don't want this

thing to just guess um answers based on

its training data it might be out of

date because you're going to update

policies stuff like that so in this case

the AI assistant will use rag to

retrieve the most relevant information

from the system it's going to generate

an answer based on that specific

information which makes the AI far more

reliable and up toate for your needs

okay rag is a pretty simple concept to

wrap your head around now we're going to

move into databases which I think are a

little more complicated but once you

really break them down not that bad so

in order to make rag work the system

needs a way to store and retrieve data

efficiently this is where the vector

databases are going to come into play so

in simple terms Vector databases store

data in the form of vectors which are

just numbers that represent the meanings

of words or text or whatever it is and

it's going to store these vectors into a

multidimens dimensional database so

these vectors are going to help us find

find similar or related information much

quicker than sort of like a relational

um structured database this one's going

to be using a lot more unstructured data

so even if the words are not the exact

same for example you're asking about

cars the vector database might also help

you find related information about

vehicles or automobiles as you can see

in this picture down here we've got um

wolf dog cat and then the query is a

kitten so it's going to be searching for

a kitten information about kittens and

it will kind of be um in this

three-dimensional

database store it'll be seeing like

similarities based on characteristics of

these things and as you can see like

we've got fruits over here and then you

might have vehicles down here and you

might have like you know information

related to certain types of products up

here so that's kind of how this works

just as like from a visual perspective

so if you're wondering how Vector

databases work in relation to rag the AI

is going to convert documents or text

into Vector stores and it's going to put

them in the vector database where they

need to be then when a question is asked

the system is going going to look for

similar vectors and sort of search out

the right area to pull information back

um you know relevant documents or data

and then once it finds these most

relevant vectors it's going to retrieve

that information and then finally it's

going to generate an answer for the

human once you understand what a vector

database is what Vector stores are you

need to understand how can you actually

get information into a vector store so

this next slide is going to talk about

sort of embeddings and stuff like that

all right so embedding data into a

vector database this this slide is going

to be kind of tailored towards doing

this in n8n there's other ways to but NN

is the way I do it so real quick let's

just break down this picture so what's

going on here is we're testing the

workflow it's going to be searching a

Google Drive for a specific file it's

going to pull that file and then we need

to embed it into the pine cone Vector

Store Pine Cone is just a vector store

database that we use um it just seems to

be you know very cheap very easy to use

so this is the one we're using but

there's other Vector databases out there

you might have heard of something like

super base but this one's really simple

then what it's going to do is it needs

to load the information so the type of

information coming through whether it's

Json or binary it's going to load that

it needs to be able to split it up you

know it's going to chunk it up and then

it's going to use the open AI model to

embed it into the actual Vector store so

I know that this stuff may not make

sense yet we'll get into an actual

example in NN where we're building this

out and we're getting real PDFs from our

Google Drive up into pine cone and we'll

see all that take place but we just

wanted to give you a quick visual real

quick quick so you can understand what's

going through the first thing I'll touch

on real quick um is the default data

loader aspect of this so in NN when we

connect the vector store we have to load

the data this node is basically just

going to allow us to load data from a

previous step flowing through um you

know right here and then we need to load

it into here so that we can actually

chunk it up and get it embedded into the

vector store so this note is pretty much

just going to be looking at what kind of

data we're loading in um if it's like

Json or if it's binary that sort of

stuff and then we can just you know

configure how much we want to pass

through stuff like that and then we move

into actually text splitting so right

here I have a recursive character text

splitter as you can see right here the

three options in NN will be character

recursive character or by tokens so the

first option is character text splitter

this is just going to split the text

into chunks based on a set number of

characters so you might want to use this

when you want to break down text into

equally sized pieces regardless of where

sentences or paragraphs end um and then

the next one we have is recursive

character text splitter which I seem to

use the most because this one is going

to split text by characters but it does

so intelligently because it's going to

break down logical points like after a

sentence or in between paragraphs stuff

like that but same concept of just

chunking stuff down so this is

recommended when you want to keep the

text meaningful instead of cutting off a

sentence in the middle it's going to

split at natural breaks like after you

know a period or a comma something like

that and then finally the token splitter

this is going to split text based on

tokens which are usually words or

subwords that the model understands and

you kind of want to use this when you're

working directly with a language model

like Chachi BT because it's going to

process text in terms of tokens and you

know it's going to chunk It Down based

on how the AI model reads the text so

you know if you're processing data for a

model it's going to split the text

accordingly hopefully I didn't confuse

you guys too much maybe I went into too

much detail but just wanted to break

down those different types of splitting

but best practic is a lot of times you

can just use recursive character so the

information stays meaningful but um just

a quick summary here so the rag is going

to be um retrieving information from

documents right here that we're putting

into a vector store in order to give us

intelligent answers then the vector

database is going to store text in a way

that allows us to quickly and

efficiently search based on meaning not

just exact words that are you know

hardcoded in we're looking at stuff

that's related to specific meanings of

words and then we're going to use a text

splitter to um help break down the large

documents into manageable pieces in

order to put them into to the vector

database and then open I AI here in this

case is just going to embed it into the

vector store so that is basically how

it's going to work and we'll hop into NN

and actually show you guys this as you

can see what we're going to do here is

build an RG rag AI agent and in this

workflow we'll be using a Nike earnings

PDF and we're going to put that into

pine cone which is the vector database

that we'll be using and then we can chat

with the agent in order for it to

retrieve information about Nike earning

so that we don't have to read through

the PDF we you can just ask questions

about it all right like I said we're

going to be looking at this PDF of Nike

earnings reports so we're going to see

this is the PDF that we're looking for

it's 10 pages we don't want to really

have to read this thing we want to be

able to just chat with an agent and it

can pull the information for us so first

up here get some sort of document that

you want to put into pine cone Vector

store then as you can see I have this in

my Google Drive right here so that we're

able to actually you know call this

information and push it into pine cone

through nn and then you want to go into

pine cone it's just type in Pine cone.

it's free to get started you want to set

one up you'll come into here and all you

want to do is you're going to create an

index so you can name it whatever you

want um I'm pretty much just going to

keep everything as is the only thing

that you want to make sure that you set

up here is right here you want to set it

up by model and you want to choose text

embedding three small so you'll set that

configuration and then you'll just hit

create index your index is going to pop

up right here if you click into it you

can see that there's no information you

can see that there's no name spaces in

here um just a really quick explanation

of name spaces you can have different

name spaces within each index like let's

say I was in here and I had one for um

internal documents and then I had one

for um client a and then I had one for

client B that's just going to help your

agent be able to search for the

information quicker because it can sort

of break it down by okay I need to go to

this index and I need to go to this

namespace and then here's all relevant

information regarding this project or

client once you've got all that

information set up we are good to hop

into to NN and start pushing information

into that pine cone Vector store so the

first thing that we're going to do here

is I'm just going to make this a manual

trigger in the future you could have

this where every time you upload a

document to a certain drive it would do

a Google Drive trigger and then it would

automatically push that information into

pine cone which is super cool because

then your database is going to you know

stay up to date every single day every

single time you add more information but

right now we're just going to be doing a

manual trigger next thing we need to do

is add a Google Drive node because we

need to get that information from Google

Drive drive into NN so we're going to

click on this plus button going to type

in Google and we will see Google drive

right here once again lots of actions

the Integrations are awesome but what

we're going to do here is download a

file so if you haven't got this node

configured yet it should be super easy

because you've already set up your

consent screen and your client ID and

secret and all that but in here you just

need to go and make sure that you have

enabled the right API so as you can see

here I've got Google Sheets Google Drive

Gmail Google Docs custom search all the

different apis that I can use within in

NN so set that up make sure you're

connected to the right account and then

we're going to be downloading is the

operation and we're grabbing a file the

resource and once again we can choose

from a list which is awesome we're going

to come in here and look for the Nike

press release PDF so I'll grab that and

then what we're going to do is just hit

test step because then we can see the

information coming

back so on the output you can see that

we're getting this information one thing

that's really important to know is that

it's not coming through as Json there's

no information here it's coming through

as binary so we don't have to get too

technical on what exactly that means but

we have to just make sure we know how

this information is coming through so

that later when we want to embed it into

the vector store we can make sure it's

getting loaded correctly and I'll I'll

show you guys that later but for now

just remember that this PDF is coming

through as binary so we can view this

PDF make sure it's the right one as you

can see it's Nike earnings so we're good

to go here and we can move on to the

next step we've got our file next we

need to add the actual pine cone Vector

store so so we can push the information

into pine cone so we're going to add

this we've got four actions within pine

cone right now we're just going to be

adding documents to a vector store but

as you can see you could also retrieve

you could update all that sort of stuff

and we will be retrieving later in order

to actually chat with our agent about

this PDF once again it's a little

Annoying to have to set up the

credentials for everything but once you

have them you're good to go so in here

we need to set up the pine cone I'm

going to create new credential and as

you can see we need to grab an API key

once you hop back into pine cone you can

see obvious you've got your indexes on

the left hand side you can go down to

API keys and then all you're going to do

is just copy this value with this button

right here copy that and then you're

just going to really quickly paste that

into the API key hit save and it should

go green because our connection is

successful now we're actually able to

insert documents to the index so the

index that we want to insert to is

called sample and for the sake of this

video let's add it to a namespace so

click on ADD option Pine code namespace

and we will just call this one

Nike and now we're good to go with this

node but what we need to do is we need

to set up like I talked about earlier

the the default document loader how

we're going to check Chunk Up the text

and then the actual embedding so first

we will do the embedding I'm going to

use open AI you you should have your

credential already set up and then we

need to choose the model so if you

remember when we set up our pine cone

index we set up the model of text

embedding three small so we don't want

to do Ada O2 we want to come in here and

grab three small so that it's being

being embedded

properly then we need to choose this

plus button and we're going to do the

default data loader like we mentioned

now here is what I talked about with we

need to remember how the information is

coming through this Google Drive so

remember we came in here we see the

output is binary not Json so binary is

how we want the information to come

through so in the data loader we need to

make sure we're selecting the type of

data is going to be binary otherwise

you're probably not going to get any

information put into pine cone so we're

good to go here the last step is just to

set up the text splitter so like I

talked about the differences between

these three as you can see there's also

a short little description here so if

you forget you can always come in here

and read what they do but we're going to

choose recursive character text splitter

the chunk size like we talked about is

just how many characters are going to be

within each chunk and the overlap um we

don't want to have any overlap and chunk

size 1 th I'm sure that's fine for now

the PDF is pretty big but we can see how

this works so let's just hit save and

then we will test out this workflow so

it's a manual trigger so we're going to

hit test workflow it's going to grab the

file download the PDF as you can see it

went through the data loader it went in

here and then it had to embed it until

it came into the actual Vector store so

let's hop back over to Pine Cone let's

go to our database let's go to the index

called sample we can see that we have

information in here now and if we click

on names spaces we will see that we just

created a name space called Nike and

there are 29 vectors in here and as you

can see 29 items left the pine cone

Vector store node all right our

information has been successfully put

from Google Drive into pine cone now we

need to build an agent workflow that

we'll be able to chat with in order to

get answers from this PDF all right

we're in a new workflow here and once

again we got to add a trigger so the

first step is going to be a chat message

because we want to talk to the agent in

order for the workflow to start

execution so we'll click on chat message

we can leave this as is because we'll be

using this button down here to actually

you know talk to the agent and that

that's how it's going to work but we

have our chat message trigger now we're

going to add a new node we can come in

here to Advanced Ai and we see there's a

ton of different AI things we can do um

there's even some templates up here to

see you know what's possible and you can

download those and start playing with

them but we're just going to come in

here and grab an AI

agent now within this AI agent you have

different types of Agents you can use

you've got tool conversational or openi

functions agent you can read a little

bit about what each of these do but

because we're giving these agent

different tools I think that we'll just

keep this one as a tools agent come in

here and call this guy our Nike agent

and then you can also do things like add

a system message you can return

immediate steps you can have him have a

max amount of iterations we will add a

system message right now it's just going

to say you're helpful assistant we can

set this up in a sec once we get all the

tools configured but this is where we

sort of tell the agent you know this is

your job here's background information

here are the tools that you have here's

how you use them here's like an example

flow so we'll talk about all that after

we get the rest of this workflow

configured we've got our Nike agent and

then you can see there's different

things we need to set up so the first

one is going to be the chat model I'm

going to grab an open AI chat model and

connect our credential once again and

then we choose the type of model we want

since this is going to be pretty

conversational I think I'm going to use

40 it just seems to be the most

consistent it's kind of the one that I'm

pretty loyal to but sometimes for

smaller things like if you're just

labeling emails or if you're um doing

some sort of classifier where you just

need to parse the information and see um

like a category maybe then you could

come in here and grab you know 35 or 40

mini but don't get too caught up on what

each model's good at but right now 40 is

kind of the most expensive but it is the

most

powerful so we set that up with 40 now

let's really quickly add a memory so

this is super super easy we just want to

grab a window buffer memory um this is

super easy because that's all we have to

do we don't have to set anything up you

could change the context window length

but five chats is how many the model is

going to remember so I'm fine with that

but this is a really easy way to give

the agent some context of what's going

on otherwise when you're chatting with

it let's say you asked um what was

Nike's earnings in you know quarter 3

and then if it came back with the

information and then you said okay what

about quarter 4 it would be like what

are you talking about quarter 4 for what

so that's going to give context of oh he

just asked about earnings now he wants

to know about quarter the next quarter

so just just going to give context to

your agent super easy way to add that

memory then finally this is where all

the magic happens this is where you can

add different tools So within here we

have you know different things that we

can give our agent access to of course

we've looked at all the different nodes

and the actions they can take but we can

see here that this is where it's really

powerful because we can call an NN tool

or an NN workflow as a tool so that

workfl that we just made about um you

know getting information into pine cone

we could call as a tool here but that's

not exactly what we're going to do we

are just going to call um sorry a vector

store

tool and this is the one that's going to

be getting our um Nike information so we

will just call this um database and then

you need to give it a description of

when to use this tool so we'll say call

this tool to um read to get get

information about Nike's

earnings to answer the user

question okay so that is the description

for this tool now we need to set this up

with the actual Vector store because we

need to connect this to Pine Cone and

then a model of course so let's add the

model real quick pretty much same exact

thing we're just connecting the

credential we're adding a model I'll

just do foral mini here um and then we

can see we need to grab the vector store

so we have in memory we have different

options here super base that I talked

about but this is how we actually want

to work with data within our pine cone

Vector store so we're going to click on

that

um I'm going to set this up real quick

and now we see there's different

operations this is the time we want to

actually retrieve documents we don't

want to put anything in there right now

we're just trying to get information so

we'll click retrieve we need to choose

the index that we want which is just

sample and then here's another option

where we can add the name space for this

agent to go search through so we called

ours Nike so make sure you put the right

name space in here and make sure it's

spelled correctly too so now we have

that set

up so we're almost done with this agent

last thing we need to do here is ADD the

embedding which once again we did um

three small so we need to set up three

small once again okay so this is pretty

much it for this agent we should be able

to talk to it and have a conversation

with it now so let's hit save and let's

just give it a shot so real quick let's

go to the PDF and ask about something so

we can see the gross margin for the

fourth quarter increased 110 basis

points to

44.7% so let's ask about um the gross

margin for the fourth quarter so we'll

come back into nnn we'll chat with his

agent um we'll just say how was

Nike's um gross margin for

the fourth quarter see what he

says Nike's gross margin for the fourth

quarter was

44.7% so that was right that's the

information we're getting but we maybe

don't like the way that this agent's

talking to us so that's where we need to

actually come back into the agent and

prompt it so let me just type out a real

real simple prompt and then we will take

another look all right I went into chat

gbt and I said hey can you help me

prompt this agent it needs to understand

its role some context instructions I

want to give it some example flows of

how it should operate and we got a

pretty good prompt out of it so let's

just read through it real quick we said

you are a friendly and helpful Nike

representative tasked with answering any

questions users may have about Nike's

earnings you have access to a vector

database with all the relevant data on

Nike's financial performance including

Revenue profits other earning related

info when a user asks a question you

should search this database to find the

most accurate and up-to-date information

and respond in a friendly approachable

tone be sure to add humor and use emojis

to make the conversation fun and

engaging then we gave it instructions

for an interaction flow so basically we

said a user asks a question you're going

to search the database you're going to

respond and then we gave it some

information or some examples of a

friendly tone greeting the user throwing

emojis using jokes um all that kind of

stuff and then we wanted to give it a

sample flow sort of like more exact um

the more examples that you can give an

agent about you know what it might run

into different situations the better and

then finally we said the actual tools

that it has so Vector database is really

the only tool we hooked up and we said

to use this to retrieve specific

earnings information and financial

performance remember your goal is to

provide accurate data while keeping the

user engaged with humor emojis and a

conversational tone all right so let's

give this a save and ask another

question let's let's just come in here

and say um who is Matthew friend because

he's the Executive Vice President and

CFO of Nike so we'll say who is Matthew

friend and like what did he say I guess

let's see what we get from

that who is Matthew friend and what are

his

thoughts okay so here's what we got from

the agent Matthew friend is the

executive VP and CFO of Nike he's the

financial Mastro and ensuring the Swit

stays profitable and Innovative and then

we have um two emojis there let's see he

said he G the agent gives us the quote

that he said and then at the end it says

if you have any more specific aspects

you're curious about I can dig up his

latest commentary for you so good emojis

very friendly um let's just say sure can

we get some more

info and this is information this is

important because it's going to remember

what we were just talking about which

was Matthew friend and we can see if

there's anything else in this PDF that

he said um so here's a slice of wisdom

from Matthew friend the CFO he recently

highlighted that while Nike is driving a

better balance across his portfolio the

fourth quarter brought some challenges

but no worries he's on it Matthew

emphasized that Nike is taking strategic

actions to reposition itself for

sustainable profitable long-term growth

okay so we're seeing a conversation with

this agent right here in the log you can

see exactly what's happening so you can

see our agent um it updated the memory

it went to the chat model it read

through it prompt and then it basically

is like making sure it knows what to do

it's going to go to the vector store

tool and we have the query which is

Matthew's friend Matthew friend's recent

statements or comments and then it got

an output from the um pine cone database

so if you don't understand what's going

on here basically it's just being able

to see the flow of what's going on so

that you can um you know troubleshoot if

need be but this is super cool and it

just shows you how you can connect

different tools so we could even come in

here and add a um what is it Wikipedia

so this is going to let it search in

Wikipedia so if there's information

maybe that's not about um that's not on

this PDF it could also access this tool

and we'd have to obviously prompt it a

little bit to do that but let's just see

if this is going to work we can say what

is the capital of Florida and it should

be searching through wikkipedia to

answer that question so the capital

Florida is Tallahassee it's not just

about beaches and theme parks haah nice

and friendly but um you know this

information the capital of Florida I

doubt that it was on this earnings

report from Nike so that just shows you

that it actually went and searched

through this tool and you know you can

also add like a calculator in case you

want to make sure it's doing you know

math

accurately um so we got a calculator

tool here now too so we would prompt in

that but it's super cool because like I

said you can connect different workflows

that you build within NS tools so let's

say we have this agent here and we give

it a tool that um can send emails

because we're going to build a workflow

of automatically sending an email and

and then we would just give the agent

this this tool so that if we wanted to

chat with the agent and say hey by the

way could you send this information to

um you know Matthew friend in an email

and it would actually be able to go to

do that as long as it had Matthew

friend's email which we would give it in

some sort of vector store as well so um

I hope that that you know is a breaks

down the concept of rag Vector databases

um pine cone Vector store how you can

link all these together when it comes to

giving an agent access to all these

different things in order to do what you

wanted to so at the end of that last

build we saw we started expanding on

that agent and giving it access to you

know Wikipedia and a calculator tool and

so I wanted to talk a little bit more

about how you can actually expand on

these agents to make them even more

powerful and scalable um you know like

giving an agent access to more tools

giving an agent access to agents to call

on it's it it's super powerful the stuff

you can do so in this part just wanted

to quickly talk about building workflows

as tools how that all works how that all

comes together and the importance of it

and then we'll just go through a couple

examples in NN of some agents that I've

built and you can just see the way that

they use different tools all right the

power of being able to build custom

Tools in NN it's it's honestly insane so

first we have the fact that agents can

use these tools obviously you can build

a tool and have an agent call on it like

in this example down here you can see um

I have get email tool send email tool

update database summarize database set

calendar event and get calendar all of

these are tools that I built within nadn

so these are workflows I'll show you

guys them once we hop back into nadn but

these are all different tasks that I

built out in nadn and then the agent is

able to decide based on what I tell it

texting it on telegram based on what I

tell it to do it will decide which tool

to use in order to go complete that task

and then it will either tell me that it

did the task or it will give me you know

the summary of a database or my calendar

that sort of stuff so agents can use

these tools um you know like a smart

agent or a smart AI assistant that can

call these workflows so this is a great

example right here of a personal agent

we also have the fact that tools can be

reused and recombined so now that I have

these tools built out I have a send

email tool if I ever need to build a

different type of agent to send emails I

can just give it this tool I've already

built it so it's already there in my

workflow and I can call on it in

multiple different agents it won't

really matter so that is super cool they

can be reused anytime and they can be

combined with other tools and now for

scaling so this is what I talk about the

fact that as you build out tools you

just have more and more tasks that you

can complete um more things that you can

give your agent to do and then it gets

even more powerful because um let's say

you want to not just have a send email

tool but you want to have an agent that

can do everything within email so you

would have an agent and you would give

it a ton of different tasks and email so

youd have an agent with get emails send

emails label emails draft emails delete

emails all this kind of stuff and then

you could give your overarching like

larger agent access to the agent that

does email stuff so this agent would be

able to decipher okay do I need to go

into Outlook or calendar or teams or

slack and then you would down here have

one agent that does everything in slack

One agent that does everything in teams

One agent that does everything in your

calendar and then you can just build on

top of each other and also that's going

to make your workflows more efficient

rather than trying to you know send a

prompt through with like giving this

agent you know 50 to 60 tools like that

would be way too much even I think like

20 is probably too much but that way you

could give the agent other agents and

it's just like you know the hierarchy of

it's going to go through this guy then

it's going to go to these agents and

then it's going to come back so it's

just you can get really creative here

with how you can get stuff done and all

you have to do is break it down by tasks

so take a task and combine these with a

larger workflow of getting all these

tasks done and then you know larger just

just scale up pretty much so now let's

just hop into nadn and we can take a

look at you know this assistant and a

couple other ones all right so this is

the personal assistant that we were just

kind of taking look at back in the

slides but as you can see it's got just

pretty much seven tools it's got

database information so for something

like getting or sorry sending emails it

needs you know contact data information

who do I actually send it to what's

their email address and then we have

these different tools get emails send

email get calendar set calendar and then

update or summarize the database so real

quick I'll just show you guys how I

talked about these ra all tools within

my nadn so if I go back here we can see

um here's the update database tool

here's the calendar email so we can like

click into one of these so let's do

summarize database as you can see it's

just a very simple workflow we've got

different nodes we've got um the actual

database it's going to call on this

database it's going to summarize it

aggregate everything into one clean

field and then it's going to send the

response of the information back to the

agent so it's going to go through this

process then it's going to have a

summarization right here once we get

that information summarized it's going

to go back to the agent and then it

knows its job is done so then it's going

to Output a telegram message back to me

so real quick let's take a look at this

database this is the project database

that I'm summarizing in this case so

we've got different tools or sorry

different projects we've got notes about

the project and then we have the

different statuses so I know it's a very

simple

example but that's just you know I was

testing out this personal assistant and

trying to make a video about it so

here's the assistant let me just pull up

my telegram with my that I talked to for

my AI assistant um as you can see

there's different information that I've

been testing out with other workflows

and other executions but let's just come

in here and say can you summarize our

database and so this is going through

telegram the agent is under getting this

prompt right here can you summarize our

database it's figuring out which tool it

needs to call in order to do that and

then it's going to summarize the

database as you can see we just got this

message back here's a summary of the

current status and contents the a AI

project is complete the marketing

campaign is pending it involves drafting

content this that is ready and awaiting

review by the marketing

head um mobile app project this project

involves developing a user

authentication module which is currently

ongoing beta testing has been scheduled

indicating progresses in the works so as

you can see it's you know summarizing

all this information for us could be

super useful if you were on the road and

you need to send a quick email so you

just have to text this agent real quick

or you know on your way to a meeting and

you need to summarize get some quick

information summarized it could even

summarize all the emails you've gotten

from a certain day so that is a cool

example of um building an agent and

giving it examp giving it access to

different tools that you've built in NN

by the way if you if you want to know

more about what this agent can do please

go watch the video I'll tag it right

here um I made a whole video about you

know building this personal assistant

and sort of like the capabilities of it

and how you can expand on it so

definitely go watch that video if you

want a more in-depth look at what this

agent does here's another quick example

of a different way you can structure an

agent this one is being triggered by

Gmail so every time I got a new email

it's going to come through here it's

going to classify the email give it a

label of high priority customer support

promotion finance and billing and it

will actually give it a label on Gmail

and then for each of those types of

email it's going to come through here

and select for high priority one it's

going to create a draft and then it's

going to have the draft sitting in our

email and then what I would do is um

actually I made a video about this one

too so if you haven't seen it I'll tag

this one too and you want to you know go

look and see how this works and how to

build it but then what I did in the

video is we hooked it up to a send text

message node right here in telegram so I

configured this and then it was able to

let me know hey we made a high priority

draft for you based on this email from

Kevin and now it's like there for you

and then I did the same thing with all

these other ones so like for customer

support we let it actually create an

email and reply to it so it actually

sends off an email and then the telegram

message says um we sent off an email for

you based on you know it was a customer

support email same thing with these two

down here in you know if I pull up

telegram we can actually see these past

interactions I've had so like for a

finance and billing one down here we

wanted it to summarize the information

and then send it to the finance

department so right here we see you

received a finance and billing inquiry

from Angela from the accounts Department

we've notified your finance department

of this email um right here it's like a

promotional one so here are details

regarding a promotional email from Nate

it gives us a summary of the promotion

and then it gives us a recommendation so

that's something that we crafted out

right here and all of these were linked

up to different telegram nodes to let us

know notify us of what's coming through

and what the agent had done so like I

said go watch that video if you want a

more in-depth run through of what this

um agent does but the purpose of me just

showing you guys this real quick was

just to open your eyes about how you can

expand how you can build off of you know

different ways you can structure agents

and how you can you know make them do

exactly what you want to do and remove

yourself out of that process to automate

things so just super cool stuff moving

on to part five which is going to be

talking about apis and HTTP request

quests um this kind of stuff can sort of

get a little Technical and seem

confusing but I'm here to make sure we

just sort of break it down as simple as

possible so before we really get into

the content of this part I wanted to

just stress that you know we've already

been working with API calls and API

tools whether you've known it or not all

of the preconfigured nodes in nadn are

pretty much just HTTP requests in some

way or another so when you're using

these nodes naden is doing all that hard

work of making the API call for you you

know either fetching or getting some

data like in that previous example when

we were using that Google Drive node to

get information to put it into our pine

cone Vector store that was pretty much

an API call to Google Drive looking in

our Google Drive grabbing the file and

then we got the information back in Ann

so we're pretty much already doing that

you only will really need to use apis

and HTTP requests in nadn if you want to

connect to something that there's not an

integration for which um is kind of rare

but it's good to go over just in case

you do need to do this so yeah the an NN

they know exactly what to do exactly

where to go where to send their requests

and how to get the information you need

or put information somewhere that you

need to so now we can move into talking

about apis so what is an API it stands

for application programming interface so

basically just think of it as the bridge

that is going to allow two different

softwares to talk to each other like

nadn and Google Drive whatever it may be

so here's a concise summary about API

endpoints calls and HTTP requests so so

um the endpoint is just basically going

to be a specific URL or address within

the API where a certain service or piece

of data can be accessed so it's like the

exact path that you need to take once

you access that API you have that

endpoint so it's going to specify where

you need to go then the API call is just

that request that you're making to the

API asking it to you know perform some

sort of task or provide some sort of

data so it's like you're placing an

order and then the HTTP request is the

actual method that you use to send that

API call over on the internet so it's

sort of just the messenger that's going

to carry your request to the API

endpoint and then it's going to bring

the response back in a nutshell you're

going to be making an API call using an

HTTP request which is going to be sent

to a specific API endpoint and then

we'll get the information back from the

API and then the HTTP request is going

to return the information to

us okay so what is an HTTP request think

of this as just the way that your

computer or nadn is going to be talking

to the other service so you can do

things like get data which will be sort

of a g HTTP request or you can send data

which will be a post HTTP request which

you'll see once we hop into NN and

actually look at some examples but just

as simple as either asking for

information or sending information

somewhere I remember when I first heard

about all these different terms I

thought to myself like that sounds so

similar how do you really distinguish so

let's just quickly talk about how they

actually work together so like we said

an HTTP request is is how you actually

make an API call it's the messenger

that's going to carry your API call to

the server so we've got a quick

restaurant analogy let's think about it

like this so we have the API this is

like the restaurant itself so this is

the service that you're talking to the

restaurant is going to provide different

services to its customers you know just

like an API the restaurant offers a menu

of things that you can request different

actions or different data then we have

the API endpoint the API endpoint is

like this specific kitchen station that

you're talking to so it's going to

handle a particular dish there are

different stations for each tasks you

know cooking pasta making pizza so the

end point is like going to the correct

station in order to get the specific

dish that you

ordered then we have API call um an API

call is like placing the order it's the

actual request so in this case you know

we wanted spaghetti that's how we know

to get it to the right spot but um you

know you look you you'd order the

specific meal and then um that's just

making the request um for data or for a

specific service from the API and then

finally we have the HTTP request which

like we said is pretty much just the

mechanism that's being used to deliver

the request so in this analogy it's

going to be a waiter who's going to take

your order bring it to the kitchen staff

and then when they bring the dish the

waiter is going to bring back that food

to bring back that information that you

were looking for so hopefully that was

simple enough API call is the concept

HTTP request is the tool so you're

asking for something with an API call

and then the request is going to be how

you're delivering it over the internet

all right now let's just get into NN

real quick and just look at a few

examples of an HTTP request node and

sort of what it looks like to configure

something like that we are now back in

nadn as you can see I've got three

different HTTP request nodes in here so

you would just come in here and grab

HTTP request as you can see right here

um but these first two we've got two

gets so we'll be asking for information

in one way or another and then this last

one will show a post where we're

actually sending information somewhere

so let's just go into this first example

here

so this one's going to be a really

simple one we're making a get request

like I said so we're asking for

information here would be like sort of

that API endpoint like we talked about

so we're going to be going to

openweathermap.org um we're going to be

asking for weather you can see here's

some parameters Q equals New York so

we're looking for weather from New York

and then we have a little credential

here we had to set up an API key to

actually be able to access um the API of

open weather map and get into you know

that's my API key so it knows that we

have permission

and we'll hit test step here so we can

just see that this request is working we

can see information coming through on

the right hand side we've got clouds

we've got temperatures we've got wind um

and then as you can see it came back for

the name the city of New York so we know

that this request was working I won't go

too much right now into you know setting

up parameters and headers and body for

your request but usually when you want

to connect to a certain API they're

going to have documentation on it so in

this example for open weather map they

have exactly like the end points that

you need to find or they they'll give

you what you need to type in and how to

specify parameters it's not like you

have to know how to just find the stuff

cuz that seems pretty technical um so

yeah most of the things that you want to

connect to if there's not an integration

in NN already we'll have documentation

on their website of how to connect to

different things how to request for

different things how to send different

things so you'll just have to read

through documentation but another cool

thing obviously like we were getting

weather from open weather map but as you

can see like open AI already or sorry

nadn has Integrations for this where

it's a lot easier because this is

basically setting up that API call they

just did all the coding the technical

stuff on the back end of that so we have

this basically the exact same thing okay

so this next one is another get request

this one is as you can see we're going

to be searching Google so we have the

endpoint right here of google.com/

search but we did want to set up some

parameters here so we have q like we saw

that last one Q equals New York this

time Q is equaling site colon

linkedin.com

slin okay so this is the URL that we're

basically trying to access so if we p

ped this into Google right here we would

see like it brings us up Google so

that's what we're searching on and then

within Google we want to be searching

for site umon linkedin.com so we go back

to Google paste that in there and you

can see what's coming back is actual

LinkedIn just LinkedIn profiles so

that's sort of how this parameter is

working and we can go ahead and test the

step real

quick we can see exactly what's coming

back which is going to be a nasty chunk

of HTML a lot of information in here

your next step here would be to parse

through this information with a

different node that would grab you just

LinkedIn profiles so like if I come in

here and search um linkedin.com you can

see like I'm sorry we've got a lot of

hits 173 hits and we can sort of go down

until we find actual profile so that's

what you'd have to be parsing out but

right here we have Robert W Livingston

so if we go back to the actual Google

search we can see that first profile

coming through is Robert

Livin um and then if we were to continue

to go down and look through all the

different results we'd see all these

different profiles coming through into

our naden so that is the way that this

request is asking for information from

site colon linkedin.com in and then

we're actually getting back the

parameters from or sorry the information

from Google through that request and for

this final one we're making a post

request as you can see right here so I

click into this we'll see what's going

on in this node this is a post request

and I was able to go to Google apis in

order to see how to access my calendar

there's going to be different API

endpoints in their documentation of like

you know copy this URL if you want to

create event copy this URL if you want

to update an event copy this URL if you

want to get information back on your

events so that's all I did I I hooked up

that that API endpoint in here obviously

had to set up my credentials and then in

this example we have to send a body

because we're posting data sending

information and so this is really simple

it's just Json um sort of setting up the

criteria for the event you could you

know go into chat GPT and say hey I'm

like accessing a Google API for my

calendar can you help me set up a body

and it should work with you there but in

this case the summary of the event that

it's going to be making is meeting with

team we have a start date um noon we

have an end date of 1:00 and then we can

add like attendees and different emails

and real quick I'll show you this is the

calendar that I'm accessing right here

so there's nothing going on today and

we're going to make the event for noon

so if I hit test step it'll come through

and it'll say that it worked and we can

see on here we just got our meeting with

Team from noon to 1:00 p.m. and the

information coming back here is just

going to be like you know meeting link

it's just going to basically tell you

that that post request went through

successfully all this kind of stuff but

another case where that would just be

over complicating things you've got

Google Calendar right in here um where

is it right here we can get availability

we can create an event so all we did

right here was create an event this is

going to make it a much easier way to

actually send that request because you

just have to fill in different

parameters and you don't have to worry

about the API endpoint putting that in

you don't have to worry about um you

know the Json sending over the data in

that post request you could just do that

right here as well now that that concept

of just how you access endpoints and how

you actually send or receive data makes

more sense what you would want to do

from here is like the more realistic use

case when you're building stuff like

this and you need to you know integrate

with something is going to be a web hook

trigger so you can see like you've got

your url here you have an HTT method and

this is the kind of stuff that you'd be

more familiar with setting up once you

understand the basics of um sort of

these noes but these are going to be

really powerful tools because these will

let you trigger a workflow based on um

information coming through from another

site so if you wanted if you had some

sort of form on your website and you

wanted to hook up to that and then every

time someone filled out the form you

could have this go through where it's

going to you know notify you that

someone filled out the form it's going

to send them an email sort of welcoming

them it's going to throw them into a

database and then it's going to send

slack message to your team something

like that so these web hooks can be very

powerful when it comes to automating

other processes as well and getting

pretty customized but before you get in

here and you want to start configuring

stuff I think it's just important that

you understand the the framework and the

basics of you know apis and points HTTP

requests and how all that stuff is going

to work in nadn and then you can really

explore with stuff like web hook

triggers which are very cool and offer a

lot of flexibility all right we have now

made it to part six which is going to be

the final part of this master class you

know we've covered a lot of ground we

started the basics of NN building your

first workflow we created an AI powered

agent using RG Rag and Vector databases

we made API calls and HTTP requests we

talked about extending your workflows

with custom tools and web hooks so

you're no longer a beginner you have the

tools and knowledge to create powerful

automations that are going to transform

your productivity the way you approach

your automation projects and I just

wanted to close off with talking about

error workflows um just sort of best

practices when it comes to creating

workflows in na then and sort of how you

can do that most optimally and then um

just some final next steps and just

closing thoughts

all right back in NN here we have a

error demo workflow which is just an

error workflow that I just created real

quick as you can see it's going to start

off with an error trigger so this

workflow is going to execute whenever

there's an error and another workflow

that we're hooking up this one too so

that'll make more sense once we actually

configure it but as you can see It'll

Get triggered and then it will come in

my telegram um which will be sending me

a message so it's going to notify me

that there's an error it's going to tell

me the workflow that's erroring it's

going to tell me the error message

message that happened and then it will

give me a link to the actual execution

of the error so that would all just pop

up on my telegram I can click on the

link and come in and see what's going on

but in this case this is going to be you

know a personal assistant I showed this

a little bit earlier so this is the

workflow we want to hook up to that

error workflow we come in here up top

right grab that three dots click on

settings and then right here you can see

error workflow so a second workflow to

run if the current one fails the second

workflow should have an error trigger

node so we saw the error trigger node we

saw that this workflow is called error

demo so we've hooked that up as this

error workflow and um now we just need

to make sure that this workflow is going

to error so let's just delete the brain

of the assistant so this one should

error for sure as you can see it already

is and um it's going to be calling this

and then it's going to be filling in the

information when it airs so let me just

pull up my telegram real quick as you

can see this telegram this is my AI

personal assistant so this is how we

talk to it and this is how how it talks

to us back right here if you can see

this flow but let's just ask it to do

something like can you get my

emails this should airor and as you can

see we got the error notification the

workflow is personal assistant which is

right up here the message is that a chat

model subn node must be connected so

that's the eror that's going on right

here and then we have a link to that

execution I can click on that link and

it should bring me into what exactly

just happened and we can see why it's

erroring so as you can see this is the

most recent execution that just happened

um it's going to take a second to load

up but basically the error is just

happening because a chat model sub node

must be connected that's why it aired

and as you can see that's exactly what

it told us in

here okay so that's kind of how this

works um you know you could even go you

could expand off of this so let's say

you want to get notified um but then

let's say that we want to you know send

an email to the team that says hey this

this isn't working right now um we're

working on this to get fixed so let's

just come in here and let's send a

message

um obviously we need to set up all this

information so let me do this real quick

really quickly configured this node

obviously we're sending a message put

who you want to send it to this could be

you know a ton of different emails you

got the subjects which is going to be

error and then it's going to tell us the

error message and then the message of

the email is going to say hey team we

received an error in blank workflow

we're working to resolve the issue

thanks so if I just you know test this

step we would see that that came through

um let me pull up the email real quick

so here you can see we got the error

example error message hey team we

received an error in example workflow

we're working to resolve the issue um so

let's just quickly go back and end it in

turn off the append attribution and

we'll save this and then we can um pull

up telegram we will ask it to get the

emails again and we will get an error

notification in our telegram right here

but then we should also get a new email

with that information coming through um

so we'll just give this one a sec here

okay now we got an error a chat model

sub node must be connected hey team we

receiving error and personal assistant

where we're going to resolve the issue

so obviously that's just a very quick

example email um you could configure the

subject and the message however you want

but that's just goes to show how a quick

error workflow you can set that up you

can hook it up to multiple different um

agents multiple different workflows that

you have that when they when they error

this logic will take place and you'll

get notified right away so that's just

another cool feature of net all right if

you guys have made it this far really

appreciate you sticking it through all

the way hopefully this has been a really

helpful session but before we close out

let's quickly go over some best

practices for workflow optimization to

ensure that your workflows are staying

efficient maintainable scalable and you

know all this kind of stuff as you build

out more complex automations so the

first thing I wanted to touch on real

quick is just keeping your workflows

organized as they grow you got to keep

them well organized it's going to save

you a ton of time down the road when you

realize uh oh like we have to redo this

or there's a problem and now we are all

confused about what's going on here so

make sure you use you know descriptive

node names you can throw in comments

really easy with a little sticky note um

you can you know make notes in your

workflow so that if anyone else wants to

come in and look at what's going on or

wants to help you out in the future they

can quickly understand what the workflow

is doing what each part of the workflow

is doing then we want to be able to use

sub workflows for reusability you don't

need to reinvent the wheel every single

time you want to do a similar task in

these different workflows consider

creating subw workflows like we talked

about with you know maybe one for

sending email one for creating calendar

events and then you can hook that up to

a bunch of different agents or even have

agent that's you know a specialist in

one certain type of platform so that's

going to make it sa saves you a ton of

time later down the road when you want

to make more complex automations you

don't have to build out the same you

know five nodes that are going to be the

same staple for every single thing that

you need to do in that space um so

that's just going to save you a lot of

time and avoid redundancy and the third

thing we want to do is Implement air

handling so already talked about that a

little bit but you can even take it a

step further so you know errors are

going to happen

no no workflows immune to issues like an

API failing or something like that so if

you build in some of these issues or

error handling issues it's going to

ensure that your workflows remain robust

you can be notified when something goes

wrong you'll have like a safety net

behind each of your automations and then

finally just you want to optimize for

scalability so as your workflows get

bigger efficiency is going to be super

important so you want to use features

like batch processing or pagination you

want to have a lot of conditional logic

in there in order to handle larger data

sets more complex branching workflows so

scaling doesn't just mean bigger

workflows it also means making them

smarter workflows and next steps now

that you've made it through this master

class you built a solid foundation I

encourage you to keep pushing your

boundaries there's so much more that you

can explore in nadn and your next step

should be about expanding your skills

and experimenting with sort of more

advanced templates so in order to do

this to continue growing and learning I

definitely want to invite you all to

join my fre School Community where we

all you know share ideas workflows cool

things that we've built using nadn it's

all about collaboration and inspiration

so whether you're looking for feedback

or you just want to brainstorm new ideas

or get some questions answered um it's

nice to have a very supportive Community

to share your progress with and it's

going to make the experience a lot

better so please hop in the link for

that is going to be in the description

and I'll also be sharing a lot of

resources in there that I I use in each

of the videos and stuff like that so I'd

love to talk to you guys and I'll see

you in there the first thing here is

going to be just to get in and start

building you know the power of learning

by doing is insane a

but really anything that involve tools

like n is it's best to just learn by

getting your hands dirty you know as you

build workflows experiment with things

push the boundaries of what you can

automate you're going to run into

challenges and you're going to have some

failures but that's definitely a good

thing like it's just part of the process

and when you fail and you can go in and

figure out what happened and actually

solve that problem you're going to just

understand the process way more than

someone who you know is not actually

getting in there and doing things just

watching YouTube videos stuff like that

you even every time I build out any sort

sort of agent any sort of workflow it

always fails and it's just going to

happen but that's how you really

understand you know the logic of stuff

moving through so these moments where

you're going to gain the deepest

understanding of how n in works and how

you're able to actually improve on your

skills so you know don't be afraid to

make mistakes it's just going to happen

then I would say you want to get in and

start exploring some Advanced templates

so at the beginning of this master class

we looked at sort of the community in

nadn and the template Gallery which is

just a gold mine of ideas and pre-built

workflows so you can dive into those and

you can see how people are building

things you know there's no one right way

to build an automation so you can see

different ideas and it will really help

you sort of expand your skills there too

the third thing I would say would be to

experiment with new Integrations you

know don't be afraid to try out new ones

even though naden supports over 300

Integrations for you know popular CRM

systems social media platforms databases

um it's really important to just get in

there play around with HTTP requests

different web Hooks and see all the

possibilities of how you can automate

stuff and it's really just going to you

know expand your your capabilities and

then you can always start to build and

share your own templates once you really

get experience with um building out

different things and you you start to

get more creative with your workflows so

that'll be really cool you can share

them with the community it's a great way

to inspire others and also get feedback

on the sort of builds that you're doing

and how to optimize them so yeah that is

going to be it for the master class

those of you that made it this far I

really appreciate you taking the time to

you know sit down for however long this

video was and um just listen through all

this kind of information and I really uh

try to structure it in a way where you'd

really be able to come from a beginner

and really understand what goes on in NN

and how to just get in there and start

building some simple agents and then

just make them more more complex as you

learn but like I said that's the end so

congratulations for making it this far

thank you guys so much for your time and

I will see you in that school community


```

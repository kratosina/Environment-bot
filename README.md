import discord
from discord.ext import commands
import random
import requests

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix="$", intents=intents )


@bot.event
async def on_ready():
    print(f'We already in as {bot.user}')

@bot.command()
async def hello(ctx) :
    await ctx.send(f"Hi! I am bot {bot.user}")

@bot.command()
async def joined(ctx, member: discord.Member):
    """Says when a member joined."""
    await ctx.send(f'{member.name} joined {discord.utils.format_dt(member.joined_at)}')

@bot.command()
async def helpp(ctx) :
    await ctx.send("""Here's the command we have : 
1. $InformationAboutPollution. it will give you a brief information about
    what is pollution and the current global issue of pollution
2. $InformationAboutGlobalWarming. it will give you a brief information about
    what is global warming and the current global issue of global warming
3. $GraphicPollution. it will give you some graphic related to pollution effect on our current world
4. $GraphicGlobalwarming. it will give you some graphic related to global warming effect on our current world"""
                   )

@bot.command()
async def InformationAboutPollution(ctx):
    await ctx.send("""
Pollution is an urgent global issue with serious impacts on human health, the environment, and climate change. Air pollution, for instance, causes around 7 million premature deaths annually, primarily due to respiratory and cardiovascular diseases. 
emissions, industrial activities, and fossil fuel combustion are the main sources of air pollution, with major cities in India and China frequently experiencing dangerously poor air quality. Additionally, more than 80% of the world’s wastewater 
is discharged without proper treatment, leading to severe water pollution. Industrial waste, agricultural runoff, and plastic are major sources of water pollution, causing waterborne diseases and damaging aquatic ecosystems. Soil is also contaminated 
by heavy metals, pesticides, and industrial chemicals, reducing soil fertility and posing health risks through the food chain. Plastic pollution is a growing crisis, with millions of tons of plastic ending up in the oceans each year, contaminating 
marine ecosystems and even entering the human food supply as microplastics. Furthermore, pollution from fossil fuel combustion is a major contributor to greenhouse gas emissions, accelerating global warming, which leads to extreme weather events, 
rising sea levels, and shifting ecosystems. Global efforts such as the Paris Agreement and technological innovations in renewable energy and electric vehicles are crucial solutions, though significant challenges remain in their widespread implementation. 
Addressing pollution requires collective action to protect human health and preserve the environment.r tetap ada dalam penerapannya secara merata di seluruh dunia. Menangani isu polusi.""")
    
@bot.command()
async def InformationAboutGlobalWarming(ctx) :
    await ctx.send("""
Global warming is a critical issue that affects the entire planet, driven primarily by the increase in greenhouse gases such as carbon dioxide (CO2) from the burning of fossil fuels, deforestation, and industrial activities. This rise in global 
temperatures has led to more frequent and severe weather events, including heatwaves, droughts, and hurricanes, as well as the melting of polar ice caps and glaciers, which contributes to rising sea levels. The warming climate also disrupts 
ecosystems, leading to the loss of biodiversity and threatening food and water security. Efforts to combat global warming include international agreements like the Paris Agreement, which aims to limit global temperature rise, along with the adoption of 
renewable energy sources and sustainable practices. However, significant challenges remain, as many countries struggle to meet their emission reduction targets, and global temperatures continue to rise.""")

@bot.command()
async def GraphicPollution(ctx) :
    with open("Images/AirTrends_Flyer_opengraph.png",'rb') as f :
        picture = discord.File(f)
    await ctx.send(file=picture)
    await ctx.send("for more information visit https://gispub.epa.gov/air/trendsreport/2022/#air_trends")

@bot.command()
async def GraphicGlobalwarming(ctx) :
    with open("Images/2020-11_global_temperature-plot_columbiaU-hansen-sato_2020-12-14.png",'rb') as f :
        picture = discord.File(f)
    await ctx.send(file=picture)
    await ctx.send("for more information visit https://www.co2.earth/global-warming-update")





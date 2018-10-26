<p align="center">
  <img src="https://i.imgur.com/i6wyG8k.gif" widht="70%">
</p>  

Lavalink wrapper for Discord.NET and better than Sharplink / Lavalink.NET.

---


## 🔧`What Is It?`
Victoria is a Lavalink wrapper for Discord.NET library. It uses Emzi's code style while keeping it simple like sharplink.
Even though Sharplink is great, there were constant internal exceptions and weird code style. Victoria aims to solve that and also provide full support of Lavalink.

## 🤔 `How To Use It?`
Grab the latest release from [Nuget](https://www.nuget.org/packages/Victoria/). Add `Lavalink` to your `ServiceCollection` or make a global static property of `Lavalink` since it's not a heavy object. From there on, in your `DiscordSocketClient`'s or `DiscordShardedClient`'s ready event add

```cs

// Get Lavalink from DI or Your Global Property. 
// LavaConfig is optional, it will use default Application.yml settings.
  var node = await Lavalink.ConnectAsync(Client, new LavaConfig {
   MaxTries = 5,
    Authorization = "foo",
    Rest = new Endpoint {
     Port = 2333,
      Host = "127.0.0.1"
    },
    Socket = new Endpoint {
     Port = 80,
      Host = "127.0.0.1"
    }
  });
  AudioService.Initialize(node); // Your AudioService.
  ```
  
- Get the LavaNode & Connect to VoiceChannel Or Get an Existing LavaPlayer And Play Some Track.
 ```cs
 // Get Node by Endpoint or get the first node.
 var node = Lavalink.GetNode(new Endpoint {
   Port = 80,
   Host = "127.0.0.1"
 }) ?? Lavalink.DefaultNode;
 
 // Join 
var player = await node.JoinAsync(VOICE_CHANNEL, TEXT_CHANNEL);

// Use built in queue or make your own (No Support)
player.Queue.TryAdd(GUILD_ID, new LinkedList<LavaTrack>());
 ....
 
 // Existing
 var player = node.GetPlayer(GUILD_ID);
 
 
 var search = await node.SearchYouTubeAsync(QUERY);
 var track = search.Tracks.FirstOrDefault();
 
 player.Play(track);
 ```

## 💡 `I Want X Feature In Victoria!`
You can oepn an issue and describe your feature with massive details and make sure your feature is required on global scale.

## 🚀 `I Like Victoria! How Can I Support Her?!`
GREAT! SMASH THAT :star: BUTTON, HIT THE :eyes: (watch) BUTTON. Or, you can [Buy Me A Coffee](https://www.buymeacoffee.com/Yucked) for my hardwork.
OR you can spread the word about Victoria. None of them are necessary but it would be greatly appreciated.

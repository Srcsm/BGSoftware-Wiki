# Messages
Here you can find all the information that is needed in order to configurate messages of the plugin.<br><br>

You can edit every message that you want that is inside the language files. Most of the messages are configured (about 99% of them),<br>
and you can edit them however you want. Some of them has built-in placeholders for displaying information about the action that was done.<br>
For example, the player that did the action, the target of the action, etc.

In addition to the built-in placeholders, all of the messages support placeholders from PAPI and MVdW, which you can find on the main page.<br>
Furthermore, you can make more complex messages. For example, clickable messages with hoverable text and such.<br>

### Raw messages
Raw messages are messages that only have a message without any extras - not clickable, not sent as an action bar or anything else.<br>
These messages are very simple to be editted. All you have to do is just edit the message as a string, and that's it!<br>
They also support new lines:<br>
```yaml
RAW_MESSAGE: 'I am a raw message without any extras! &aColors are also supported! &{HEX:4e87ee}Even hex colors in 1.16 are supported!'
NEW_LINE_MESSAGE: |
  &aThis is the first line.
  &6This is the second line.
  &cYou can add unlimited lines :D
```

<br>

### Complex messages
Complex messages are messages that can have extra actions to them. Action bars, titles, hoverable text and such, are all in this category.<br>

**Action bars**<br>
You can send action bars, the messages above the hotbar, by using the following format:
```yaml
MESSAGE:
  action-bar:
    text: '&aThis will be sent as an action bar!'
```
<video src="https://bg-software.com/imgs/action-bar-example.mp4" height="300px" autoplay loop></video>
<br><br>

**Titles**<br>
You can send titles, the big message in the middle of the screen, by using the following format:
```yaml
MESSAGE:
  title:
    title: '&aThe bigger text'  # If you don't want that to be sent, set this section to ''.
    sub-title: '&6The smaller text'  # If you don't want that to be sent, set this section to ''.
    fade-in: 20  # Fade in duration (in ticks).
    fade-in: 60  # Message duration (in ticks).
    fade-out: 20  # Fade out duration (in ticks).
```
<video src="https://bg-software.com/imgs/title-example.mp4" height="300px" autoplay loop></video>
<br><br>

**Interactable Messages**<br>
You can send interactable messages that can execute commands or have hoverable text, by using the following format:
```yaml
MESSAGE:
  a:   # Random, but unique key.
    text: '&aI am hoverable text.'
    tooltip: '&6Hidden message!'
  b:
    text: '&6 I can execute commands, and I will be after the first message.'
    command: '/gmc'
```
<video src="https://bg-software.com/imgs/interactable-messages-example.mp4" height="200px" autoplay loop></video>
<br><br>

### Custom language file
Creating a new language file is very easy task to do. All you need to do is to copy the en-US.yml file, rename it with a valid language format, and that's it!<br>
You can find a list of available language formats [here](https://www.oracle.com/technetwork/java/javase/java8locales-2095355.html). After you have the new file, you can edit it with the same technics that are explained above.<br>
When a new version comes out with new messages, your custom file will be updated automatically with the new messages, but in English.


---

# How to Set Up a "Radio Channel" in Telegram: A Simple Guide for Everyone

Hi there! Today, we're going to create something really cool together: your very own "radio channel" in Telegram. This means that all text messages you publish in your channel will automatically turn into voice messages, and your subscribers will be able to listen to them, just like a real podcast or radio show!

Don't worry, it's much simpler than it sounds. We'll go step by step, and you'll definitely succeed.

The setup will only take 5-10 minutes of your time.

---

## Step 1: Preparing Our "Control Panel" – Google Sheet

Our "control panel" is a special Google Sheet where we'll store all the important settings for our smart assistant.

1. **Open the template sheet:**
   
   * Go to this link: [tg-radio-agent - Google Таблицы](https://docs.google.com/spreadsheets/d/1tprxNvegnQAbL8rsVU4eM7YzS2YEPVGaZRrxiSXIpBs/edit?usp=sharing)
   * This is the "ru version" (Russian version) of our sheet.

2. **Make your own copy of the sheet:**
   
   * **Important:** You cannot work directly with this template, as it's someone else's and is view-only. You need to make your own personal copy to be able to make changes and save your settings.
   * Once the sheet opens, click in the top menu: **File** → **Make a copy**.
   * A window will appear where you can name your copy. You can call it, for example, "My Radio Bot" or "Telegram Radio Settings". Click **Make a copy**.
   * Now your personal copy of the sheet will open. All subsequent actions will be performed in this copy.

---

## Step 2: Getting the "Brain" for Our Assistant – Gemini API Key

Our smart assistant will use Google's Artificial Intelligence (AI) to convert text into voice. For it to do this, we need a special "pass" – a Gemini API key.

1. **Go to the Google AI Studio website:**
   
   * Open a new browser tab and go to the link: [geminiApiKey](https://aistudio.google.com/app/apikey)
   * If you're not already signed into your Google account, the system will ask you to do so. Use the same account you use for Google Sheets.

2. **Create a new API key:**
   
   * On the opened page, you'll see a button **Create API key in new project** or simply **Create API key**. Click on it.
   * Immediately after clicking, the system will generate a long string of letters and numbers for you – this is your key!

3. **Copy the key:**
   
   * Next to the key, there will be a copy button (usually an icon of two squares or "Copy"). Click on it.
   * **Important:** Save this key somewhere safe (e.g., in a notepad on your computer or in your notes), because we'll need it. And don't show it to anyone – it's your personal "pass"!

4. **Paste the key into our sheet:**
   
   * Go back to your Google Sheet ("My Radio Bot").
   * Find cell **B6** (it's opposite the `geminiApiKey` label in column A).
   * Paste the copied Gemini API key into this cell **B6**.

---

## Step 3: Creating a "Messenger" – Telegram Bot and Disabling Its "Privacy"

Our assistant will send voice messages to Telegram via a special bot. And for it to do this, we need its "passport" – the Telegram bot token. It's also very important for the bot to "see" messages in the channel.

1. **Open Telegram and find BotFather:**
   
   * Launch the Telegram app on your phone or computer.
   * In Telegram's search (usually a magnifying glass icon), type `@BotFather` and select the official bot (it will have a blue checkmark next to its name).
   * Click the **Start** button at the bottom of the chat with BotFather.

2. **Create a new bot:**
   
   * Send BotFather the command `/newbot`.
   * BotFather will ask: "Alright, a new bot. How are we going to call it? Please choose a name for your bot."
   * **Come up with a name for your bot.** This is the name people will see in Telegram. For example, "My Radio Assistant" or "Voice Channel". Send this name to BotFather.

3. **Come up with a unique username for the bot:**
   
   * BotFather will ask: "Good. Now let's choose a username for your bot. It must end in 'bot'. For example: TetrisBot or tetris_bot."
   * **Come up with a unique username for your bot.** It must be in English, without spaces, and **must end with `bot`**. For example, `MyRadioHelperBot` or `VoiceChannelBot`. If the name is already taken, BotFather will ask you to come up with another one.
   * Send this unique name to BotFather.

4. **Copy the bot token:**
   
   * If the name was accepted, BotFather will send you a congratulatory message with a long string of characters that starts with numbers and a colon (e.g., `123456789:AAH...`). This is your **bot token**.
   * Copy this token.
   * **Important:** This token is your bot's "passport". Save it next to your Gemini API key and don't show it to anyone!

5. **Paste the token into our sheet:**
   
   * Go back to your Google Sheet.
   * Find cell **B2** (it's opposite the `telegramBotToken` label in column A).
   * Paste the copied Telegram bot token into this cell **B2**.

6. **Disable the bot's "Privacy Mode":**
   
   * This is a very important step! By default, bots are "private" and don't see all messages in groups or channels. We need to disable this so your bot can "see" new posts.
   * In the chat with BotFather, send the command `/setprivacy`.
   * BotFather will ask which bot you want to change settings for. Select the name of your new bot.
   * Then BotFather will offer to enable or disable privacy mode. Select **Disable**.
   * BotFather will confirm that privacy mode has been disabled.

---

## Step 4: Specifying Who Is "In Charge" and Where to Send Messages – Admin and Channel ID

For security and proper operation, our assistant needs to know who its administrator is (that's you), and which channel to send voice messages to.

1. **Find your administrator ID:**
   
   * Your ID is a unique number in Telegram. It's needed so that only you can control the bot.
   * In Telegram, search for `@userinfobot` (or `@getidsbot`, or any other similar bot).
   * Click **Start** in the chat with it. It will immediately send you your ID (it will be a string of numbers).
   * Copy this ID.
   * Go back to your Google Sheet.
   * Find cell **B5** (it's opposite the `chatId telegram` label in column A).
   * Paste your administrator ID into this cell **B5**.

2. **Find your Telegram channel ID:**
   
   * We need the ID of the channel where the bot will send voice messages.
   * **Method 1 (via a bot):** Add your newly created bot (the one whose token you pasted into B2) to your channel as a member (this will be the next step). Then send any message to the channel. After that, go to the chat with `@userinfobot` (or another ID-getting bot) and forward any message from your channel to it. It will show the channel ID.
   * **Method 2 (via Telegram desktop version):** Open Telegram on your computer. Go to your channel. In the browser's address bar (if you're using the web version) or in the channel info (if it's the app), you'll see a link like `t.me/c/1234567890_1234`. The numbers after `c/` and before the underscore (`_`) are your channel ID.
   * **Important:** Channel IDs in Telegram always start with `-100`. If you got an ID without this prefix (e.g., `1234567890`), then you need to insert `-100` followed by your ID into the table. For example, if the ID is `1234567890`, you should insert `-1001234567890` into the table.
   * Copy the channel ID (with the `-100` prefix!).
   * Go back to your Google Sheet.
   * Find cell **B8** (it's opposite the `channelChatId telegram` label in column A).
   * Paste your channel ID into this cell **B8**.

---

## Step 5: Adding the Bot to the Channel and Giving It Minimal Permissions

For your bot to be able to publish voice messages in the channel, you need to give it permission.

1. **Add your bot to the channel:**
   
   * Open your Telegram channel.
   * Click on the channel name at the top to open its settings.
   * Find the **Administrators** section or **Manage Channel** → **Administrators**.
   * Click **Add Administrator**.
   * In the search, find your bot by its unique username that you created in Step 3 (e.g., `@MyRadioHelperBot`).
   * Select it.

2. **Give the bot permissions:**
   
   * When you add the bot, Telegram will offer to choose which permissions to give it.
   * **Definitely** check the box next to **Send Messages**.
   * **Important:** You don't need to give the bot any other additional permissions. Only "Send Messages" – this is enough for it to work.
   * Click **Done** or **Save**.

---

## Step 6: Deploying the Application and Linking It with Telegram

This is the most crucial step. We will deploy our application and "link" it with Telegram so that the bot starts working.

1. **Deploy the Google Apps Script application:**
   
   * Go back to your Google Sheet.
   * In the top menu, click **Extensions** → **Apps Script**. A new tab with the code editor will open.
   * In the code editor, in the top right corner, find the **Deploy** button and click the arrow next to it.
   * Select **New deployment**.
   * The "New deployment" window will appear. Click the gear icon (⚙️) next to "Deployment type" and select **Web app**.
   * In the "Description" field, you can write anything, for example, "My Radio Bot".
   * In the "Execute as" field, select **Me**.
   * In the "Who has access" field, select **Anyone**.
   * Click the **Deploy** button.
   * Google may ask you to grant permission to run scripts. This is normal. Click **Authorize access**, select your Google account, then click **Allow** or **Grant access**. This is necessary for the application to interact with Telegram and Gemini.
   * After successful deployment, a "Deployment complete" window will appear. It will contain the **Web app URL**. This is a long link that starts with `https://script.google.com/macros/s/...`.
   * **Copy this URL.**

2. **Paste the application URL into the sheet:**
   
   * Go back to your Google Sheet.
   * Find cell **B1** (it's opposite the `linkApp 🔥 set WEBHOOK` label in column A).
   * **Paste the copied URL of your deployed web application into this cell B1.**

3. **Set the webhook (link with Telegram):**
   
   * After you paste the URL into cell B1, the text in cell **A1** (`linkApp 🔥 set WEBHOOK`) will turn into an **active hyperlink**.
   * **Click on this hyperlink in cell A1.**
   * **Important:** After clicking, a **new browser tab** will open. In this tab, you will see a short message from Telegram, for example: `{"ok":true,"result":true,"description":"Webhook was set"}`. This means that the webhook has been successfully set and your bot is now "linked" with Telegram. You can close this tab.
   * Cell **B20** in your sheet is intended to display **incoming requests from Telegram** after the webhook is set and the bot starts receiving updates (e.g., when a new post is published in the channel).

---

## Step 6.5: Launching Your Bot in Telegram

For your bot to start working and receive commands from you, it needs to be "launched".

1. **Find your bot in Telegram:**
   
   * Open Telegram and find your bot by its unique username that you created in Step 3 (e.g., `@MyRadioHelperBot`).
   * Open a chat with it.

2. **Send the `/start` command:**
   
   * In the chat with your bot, click the **Start** button or simply send it the message `/start`.
   * **Very important:** This action must be performed from the exact Telegram account whose ID you specified in cell **B5** of your Google Sheet. Only then will the bot know that you are its administrator.

---

## Step 7: Final Settings in the Sheet

Now, all that's left is to insert the remaining important settings that determine how your bot will work with text and voice.

* **B3 (promptGenerateContent):** Paste the content processing prompt text here.
  * `Your task is to prepare text for high-quality Text-to-Speech (TTS) synthesis, ensuring it sounds natural and understandable. You will receive text that may contain elements not intended for direct vocalization (e.g., abbreviations, numerical time formats, special characters, web addresses, and emojis).\n\n**Transformation Rules:\n1.  **Expand Abbreviations: Expand common abbreviations into full words.\n    *   Examples (for English): 'St.' -> 'Street', 'Ave.' -> 'Avenue'. For Cyrillic languages (e.g., Russian, Ukrainian), examples include: 'ул.' -> 'улица', 'Вул.' -> 'Вулиця', 'пр.' -> 'проспект', 'д.' -> 'дом', 'кв.' -> 'квартира'.\n    *   Important: Pay attention to the language of the abbreviation (e.g., Russian, Ukrainian) and the sentence context for accurate expansion.\n2.  **Time Conversion: Convert numerical time notations into their spoken form, as close as possible to natural speech.\n    *   Examples: '8-00' -> 'eight o'clock AM' or 'eight hundred', '19-00' -> 'seven o'clock PM' or 'nineteen hundred'.\n    *   Time ranges: 'from 8-00 to 19-00' -> 'from eight AM to seven PM' or 'from eight hundred to nineteen hundred'.\n3.  **Numbers and Symbols: Convert numbers and special characters that might sound unnatural when directly vocalized into their spoken equivalents.\n    *   Examples: '№' -> 'number', '%' -> 'percent', '$' -> 'dollars', 'грн.' -> 'hryvnias', '123' -> 'one hundred twenty-three', '2024' -> 'two thousand twenty-four'.\n4.  **Handle URLs and Associated Text: Identify and remove web addresses (URLs) from the text. Additionally, remove any short, direct labels or phrases (e.g., 'Viber', 'WhatsApp', 'ссылка', 'подробнее') that immediately precede or follow a URL and primarily serve to introduce or identify that specific link, as they are redundant for vocalization. If the URL is embedded within a more substantial sentence that provides context beyond just identifying the link, remove only the URL, preserving the rest of the sentence.\n5.  **Emoji Handling:\n    *   **Convert Meaningful Emojis: If an emoji conveys a specific, vocalizable meaning (e.g., rank, status, common concept), convert it into its natural language equivalent, ensuring it integrates naturally into the sentence structure. If a natural integration is not possible or would sound unnatural, consider removing the emoji instead.\n        *   Examples: '🥇' -> 'первое место', '🥈' -> 'второе место', '🥉' -> 'третье место', '✅' -> 'выполнено' (если грамматически уместно) или 'галочка' (если уместно как маркер).\n    *   **Remove Decorative Emojis: If an emoji is purely decorative, visual, or its vocalization would sound unnatural, redundant, or not add meaning for the listener, remove it from the text.\n        *   Examples: '🔥', '👍', '🗑️', '😊', '😂'.\n    *   Prioritize naturalness and clarity for TTS, always aiming for human-like speech.\n6.  **Avoid Robotic Repetition: After all transformations, review the text to actively eliminate unnatural or robotic repetition of words or phrases, especially those resulting from abbreviation expansion. If a term (e.g., 'улица', 'дом', 'проспект') is repeated consecutively or in close proximity, particularly when listing multiple items of the same type, ensure it appears only once, or is transformed into its plural form if appropriate for the list, for a more natural flow.\n    *   Examples: 'улица Ленина, улица Гагарина' -> 'улицы Ленина, Гагарина'; 'дом 5, дом 7, дом 8' -> 'дома пять, семь, восемь'.\n7.  **Preserve Meaning and Intonation: It is crucial to preserve the original meaning and intended intonation of the text. Do not add extraneous information; only transform existing content.\n8.  **Final Goal: The transformed text must be ready for TTS system vocalization, sounding natural as if spoken by a human, not a robot.\n9.  **Human-Readable Formatting: Ensure the final text follows the conventions of natural human narration. Use appropriate punctuation (commas, periods, exclamation and question marks), insert line breaks and paragraphs where they aid comprehension, and respect standard capitalization rules so the spoken result flows smoothly and expressively. **Crucially, the final transformed text must be plain text, free of any Markdown formatting characters (e.g., asterisks `*`, underscores `_`, hash symbols `#`, square brackets `[]`, parentheses `()` used for links, angle brackets `>`, etc.) that are not standard punctuation. Ensure only natural language words and standard punctuation marks remain, so the TTS system receives a clean, unformatted input.**\n\nCrucially, your output must consist solely of the transformed text, without any additional explanations or comments.\n\nDo not change the language of the source text - TTS (text - to - speech) must be reproduced in the original language!`
* **B4 (promptGenerateVoice):** Paste the voice generation prompt text here.
  * `Create Text-To-Speech the following conversation.\nSpeak with a clear, dynamic, and engaging tone, like a news presenter.`
* **B7 (voice):** Paste the name of the voice to be used here.
  * `Kore`
* **B9 (autoPosting):** Paste the auto-posting setting here.
  * `No` (this means auto-posting is off, and you can manage publication manually if you wish)
* **B10 (ttsModel):** Paste the name of the text-to-speech synthesis model here.
  * `gemini-2.5-flash-preview-tts`
* **B11 (textModel):** Paste the name of the text processing model here.
  * `gemini-2.5-flash-lite-preview-06-17`

---

## Important Note About Telegram's Operation:

Sometimes Telegram may not immediately start forwarding messages to your bot. This is normal and doesn't mean you did anything wrong.

* **Be patient:** After all settings are complete, it may take some time (sometimes up to several hours, in rare cases up to a day) before Telegram consistently starts sending your bot information about new posts in the channel.
* **The bot may start working on its own:** Even if the webhook hasn't fully "woken up" yet, your bot may already start publishing voice messages in the channel on its own if you write something there.
* **Check in B20:** If you publish a test post in the channel and the bot doesn't react, you can look at cell **B20**. If information appears there (e.g., a long text with message data), it means Telegram has started forwarding webhooks, and the bot sees them. You just need to wait a little for it to process and publish the audio.

---

Congratulations! You have set up your "Radio Channel" in Telegram! Now try publishing any text post in your channel, and after a while, a voice message should appear below it.

---




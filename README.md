# Professional Bug Report System for Roblox

A sleek, professional bug reporting system for Roblox games with Discord webhook integration. Features an ultra-compact UI that minimally obstructs gameplay while providing enterprise-grade issue tracking.

[![Roblox](https://img.shields.io/badge/Roblox-000000?style=for-the-badge&logo=roblox&logoColor=white)](https://www.roblox.com)
[![Lua](https://img.shields.io/badge/Lua-2C2D72?style=for-the-badge&logo=lua&logoColor=white)](https://www.lua.org)
[![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com)

## ✨ Features

### Client-Side (LocalScript)
- 🎨 **Ultra-Compact Design** - Minimal screen obstruction with center-top positioning
- 📱 **Responsive Layout** - Automatic mobile/PC detection with optimized scaling
- ⚡ **Smooth Animations** - Professional tween-based transitions
- 🎯 **Real-time Validation** - Character counter with instant feedback
- 🎨 **Modern UI** - Premium color palette with glassmorphic effects
- ⌨️ **User-Friendly** - Intuitive controls with hover effects

### Server-Side (Script)
- 🔒 **Advanced Security** - Multi-layer validation and spam protection
- ⏱️ **Rate Limiting** - Per-user cooldowns and global rate limits
- 🌐 **Discord Integration** - Rich embeds with player information
- 📊 **Detailed Logging** - Comprehensive reporting with timestamps
- 🛡️ **Spam Detection** - Pattern recognition for malicious content
- 🧹 **Auto Cleanup** - Memory management for long-running games

## 📋 Requirements

- Roblox Studio
- Discord Server with webhook permissions
- HTTP Requests enabled in game settings

## 🚀 Installation

### Step 1: Client Setup

1. Create a **LocalScript** in `StarterPlayer > StarterPlayerScripts`
2. Copy the entire client code into the LocalScript
3. The UI will automatically adapt to mobile/PC devices

### Step 2: Server Setup

1. Create a **Script** in `ServerScriptService`
2. Copy the entire server code into the Script
3. Configure the webhook URL (see Configuration section)

### Step 3: Enable HTTP Requests

1. Go to **Game Settings** → **Security**
2. Enable **Allow HTTP Requests**
3. Save and publish your game

## ⚙️ Configuration

### Discord Webhook Setup

1. Open your Discord server
2. Go to **Server Settings** → **Integrations** → **Webhooks**
3. Click **New Webhook**
4. Customize name and channel
5. Copy the webhook URL
6. Replace in server script:

```lua
local CONFIG = {
    WEBHOOK_URL = "https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN",
    COOLDOWN = 90,              -- Seconds between reports per user
    MIN_LENGTH = 15,            -- Minimum characters
    MAX_LENGTH = 750,           -- Maximum characters
    RATE_LIMIT = 10,            -- Max reports per hour globally
    EMBED_COLOR = 0x8A2BE2      -- Premium Purple
}
```

### Customization Options

#### Client-Side Scaling
```lua
-- Adjust sizes for your game
MOBILE.BUTTON_SIZE = UDim2.new(0, 25, 0, 25)
MOBILE.PANEL_SIZE = UDim2.new(0, 240, 0, 260)

PC.BUTTON_SIZE = UDim2.new(0, 30, 0, 30)
PC.PANEL_SIZE = UDim2.new(0, 320, 0, 340)
```

#### Color Palette
```lua
local COLORS = {
    PRIMARY = Color3.fromRGB(138, 43, 226),
    PRIMARY_HOVER = Color3.fromRGB(155, 70, 235),
    SECONDARY = Color3.fromRGB(255, 69, 58),
    CARD = Color3.fromRGB(35, 35, 40),
    -- Customize all colors here
}
```

## 📱 Usage

### For Players

1. Click the **⚠** button at the top center of the screen
2. Type a description of the issue (minimum 15 characters)
3. Click **📤 SUBMIT**
4. Confirmation message appears when sent successfully

### For Developers

Reports appear in your Discord channel with:
- Player name, display name, and User ID
- Account age and membership status
- Full issue description
- Player avatar thumbnail
- Timestamp of report
- Player locale information

## 🎯 Features Breakdown

### Security Features
- ✅ Input sanitization
- ✅ Length validation (15-750 characters)
- ✅ Spam pattern detection
- ✅ Per-user cooldowns (90 seconds default)
- ✅ Global rate limiting (10 reports/hour default)
- ✅ Content filtering

### UI Features
- ✅ Device-specific scaling
- ✅ Smooth animations
- ✅ Character counter with color feedback
- ✅ Hover effects on buttons
- ✅ Shake animation for invalid input
- ✅ Status messages

### Discord Integration
- ✅ Rich embeds with color coding
- ✅ Player avatar thumbnails
- ✅ Detailed player information
- ✅ Unix timestamps
- ✅ Professional formatting

## 🔧 Troubleshooting

### Reports Not Sending

1. **Check HTTP Requests**
   - Game Settings → Security → Enable HTTP Requests

2. **Verify Webhook URL**
   - Must start with `https://discord.com/api/webhooks/`
   - No spaces or extra characters

3. **Check Output Console**
   - Look for error messages
   - Verify initialization message appears

### UI Not Showing

1. **Check Script Location**
   - LocalScript must be in StarterPlayerScripts
   - Server script must be in ServerScriptService

2. **Check for Errors**
   - Open Output window
   - Look for red error messages

### Mobile Issues

1. **UI Too Large/Small**
   - Adjust `SCALE.MOBILE` values
   - Test on actual mobile device

2. **Button Not Clickable**
   - Ensure `IgnoreGuiInset = true`
   - Check ZIndex settings

## 📊 Advanced Features

### Analytics Integration (Optional)

```lua
-- In server script after successful report
if success then
    -- Add your analytics code here
    AnalyticsService:FireEvent("BugReportSubmitted", {
        userId = player.UserId,
        reportLength = #result,
        timestamp = os.time()
    })
end
```

### Custom Spam Filters

```lua
-- Add to isSpamContent function
local customBlacklist = {"badword1", "badword2"}
for _, word in ipairs(customBlacklist) do
    if string.find(lowerText, word) then
        return true
    end
end
```

## 📝 Best Practices

1. **Test Before Publishing**
   - Test on both PC and mobile
   - Verify Discord messages arrive
   - Test rate limiting

2. **Monitor Your Webhook**
   - Check Discord channel regularly
   - Respond to critical bug reports
   - Archive old reports

3. **Adjust Settings**
   - Tune cooldown based on your game
   - Adjust rate limits for popularity
   - Customize colors to match game theme

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## 📄 License

This project is open source and available under the MIT License.

## 👤 Author

**ItoRenz00**

## 🙏 Credits

Created for the Roblox development community. Special thanks to all testers and contributors.

## 📞 Support

For issues or questions:
- Open a GitHub issue
- Check the troubleshooting section
- Review Roblox DevForum for similar problems

---

**Made with ❤️ for the Roblox Community**

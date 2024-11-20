# Waynot

Waynot is a notification tool designed for use with Waybar, providing a seamless way to display notifications from the D-Bus notification system in a minimalist environment, such as Hyprland. It captures notification events and sends them to Waybar, updating the display in real-time.

## Installation

To use Waynot, clone the repository and make the scripts executable:

```bash
git clone https://github.com/yourusername/waynot.git
cd waynot
chmod +x waynot waynot-daemon
```

## Usage

### Starting the Daemon

You need to run the `waynot-daemon` script to listen for notifications on D-Bus. You can configure this to run automatically when you start your session in Hyprland:

```bash
exec-once path/to/waynot-daemon &
```

### Waybar Configuration

Add the following configuration to your Waybar configuration file to integrate with Waynot:

```json
"custom/waynot": {
    "exec": "waynot post",
    "format": "{}",
    "return-type": "json",
    "signal": 1
},
```

### CSS Styles

You can add custom styles for your notifications in your Waybar `style.css` file:

```css
#custom-waynot {
    color: #ffffff;
    animation-name: waynot;
    animation-duration: 1000ms;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-direction: alternate;
}

@keyframes waynot {
    to {
        color: #f3afa9;
    }
}
```

## How It Works

1. The `waynot-daemon` listens for notifications via D-Bus.
2. When a notification is received, it extracts the title and message.
3. The information is then sent to the `waynot` script, which formats it and updates Waybar.
4. Notifications are automatically cleared after a defined timeout (default is 3 seconds).

## Customization

You can customize the appearance and behavior of the notifications by modifying the `TRUNC` variable in the `waynot` script.

## License

This project is licensed under the MIT License.

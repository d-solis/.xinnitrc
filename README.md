# .xinnitrc
my xinnitrc consists of this:

# ~/.xinitrc
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto

function VGAConnected {
   ! xrandr | grep "^VGA-1" | grep disconnected
}
if VGAConnected; then
    xrandr --output eDP-1-1 --mode 1920x1080 --primary \
           --output VGA-1-1 --mode 1920x1080 --rotate normal --right-of eDP-1-1
fi

exec rofi &
exec pulseaudio &
exec light &
exec picom &
exec dunst &
exec maim &
exec awesome -c .config/awesome/rc.lua

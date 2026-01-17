```bash
#!/usr/bin/env bash
# play.sh - tiny terminal demo: shapes vanish when internet disconnects
# Usage: chmod +x play.sh && ./play.sh
clear
ONLINE_ART='
   ⠀⠀⠀⠀⠀⣀⣀⣤��⣀⣀⠀⠀⠀⠀
   ⠀⠀⠀⠀⢀⣾⣿⣿⣿⣿⣿⣷⣄⠀⠀
   ⠀⠀⠀⠀⣼⣿⣿⣿⣿⣿⣿⣿⣿⡀⠀
   ⠀⠀⠀⠀⣿⠛⠉⠙⠛⢿⣿⣿⣿⣿⡇
   ⠀⠀⠀⠀⣿⡀⣀⣀⣀⣀⣿⣿⣿⣿⡇
   ⠀⠀⠀⠀⢿⣷⣿⣿⣿⣿⣿⣿⣿⡿⠀
   ⠀⠀⠀⠀⠀⠈⠉⠉⠉⠉⠉⠉⠁⠀⠀
'
ONLINE_SHAPES='
[■][■][■]
[■][ ][ ]
  ▲   ●   ◆
'
OFFLINE_ART='
   ⠀⠀⠀⠀⠀⣀⣀⣤⣤⣀⣀⠀⠀⠀⠀
   ⠀⠀⠀⠀⢀⣾⣿⣿⣿⣿⣿⣷⣄⠀⠀
   ⠀⠀⠀⠀⣼⣿⣿⣿⣿⣿⣿⣿⣿⡀⠀
   ⠀⠀⠀⠀⣿⠛⠉⠙⠛⢿⣿⣿⣿⣿⡇
   ⠀⠀⠀⠀⣿⡀⣀⣀⣀⣀⣿⣿⣿⣿⡇
   ⠀⠀⠀⠀⢿⣷⣿⣿⣿⣿⣿⣿⣿⡿⠀
   ⠀⠀⠀⠀  (╯°□°）╯︵ ┻━┻   OOPS
'
OFFLINE_MSG="404: Shapes not found — Did someone unplug the internet?"

# ping target (change if you prefer)
TARGET="1.1.1.1"

while true; do
  clear
  if ping -c1 -W1 "$TARGET" >/dev/null 2>&1; then
    echo "Status: ONLINE — Shapes loaded. Mario feels cute, might save the day."
    echo
    printf "%s\n" "$ONLINE_ART"
    printf "%s\n" "$ONLINE_SHAPES"
  else
    echo "Status: OFFLINE — The void is hungry."
    echo
    printf "%s\n" "$OFFLINE_ART"
    echo "$OFFLINE_MSG"
    echo
    echo "(Shapes will reappear when the internet remembers its job.)"
  fi
  sleep 2
done

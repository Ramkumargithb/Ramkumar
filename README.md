import random
import curses

s = curses.initscr()
curses.curs_set(0)
sh, sw = s.getmaxyx()
w = curses.newwin(sh, sw, 0, 0)
w.keypad(1)
w.timeout(100)

snk_x = sw//4
snk_y = sh//2
snake = [
    [snk_y, snk_x],
    [snk_y, snk_x-1],
    [snk_y, snk_x-2]
]

food = [sh//2, sw//2]
w.addch(food[0], food[1], curses.ACS_PI)

key = curses.KEY_RIGHT

while True:
    next_key = w.getch()
    key = key if next_key == -1 else next_key

    if snake[0][0] in [0, sh] or \
        snake[0][1] in [0, sw] or \
        snake[0] in snake[1:]:
        curses.endwin()
        quit()

    new_head = [snake[0][0], snake[0][1]]

    if key == curses.KEY_DOWN:
        new_head[0] += 1
    if key == curses.KEY_UP:
        new_head[0] -= 1
    if key == curses.KEY_LEFT:
        new_head[1] -= 1
    if key == curses.KEY_RIGHT:
        new_head[1] += 1

    snake.insert(0, new_head)

    if snake[0] == food:
        food = None
        while food is None:
            nf = [
                random.randint(1, sh-1),
                random.randint(1, sw-1)
            ]
            food = nf if nf not in snake else None
        w.addch(food[0], food[1], curses.ACS_PI)
    else:
        tail = snake.pop()
        w.addch(tail[0], tail[1], ' ')

    w.addch(snake[0][0], snake[0][1], curses.ACS_CKBOARD)



- 👋 Hi, I’m Ramkumar S
- 👀 I’m passionate about DevOps Engineering
- 🌱 I’m currently learning Basics about Kubernetes, AWS, jenkins,..etc.
- 💞️ I’m looking to collaborate on DevOps
.

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/grafana/grafana-original.svg" height="30" alt="grafana logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/prometheus/prometheus-original.svg" height="30" alt="prometheus logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" height="30" alt="docker logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="30" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kubernetes/kubernetes-plain.svg" height="30" alt="kubernetes logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ansible/ansible-original.svg" height="30" alt="ansible logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="30" alt="html5 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="30" alt="css3 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="30" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" height="30" alt="github logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" height="30" alt="git logo"  />
</div>

###

<div align="left">
  <img height="20" src="https://d2gbo5uoddvg5.cloudfront.net/images/Logo_aws.gif"  />
</div>

###

<div align="left">
  <img height="20" src="data:image/png;base64,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"  />
</div>

###

<div align="left">
  <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=#&style=for-the-badge" height="20" alt="linkedin logo"  />
  <img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14837&logoColor=white&labelColor=#E72929&style=for-the-badge" height="20" alt="gmail logo"  />
</div>

###


<!---
Ramkumargithb/Ramkumargithb is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

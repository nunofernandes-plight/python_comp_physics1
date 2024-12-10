import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

def wave_equation(u, c, dx, dt):
    """
    Updates the wave displacement using the finite difference method.

    Args:
        u: The current wave displacement.
        c: Wave speed.
        dx: Spatial step size.
        dt: Temporal step size.

    Returns:
        The updated wave displacement.
    """

    u_new = np.zeros_like(u)
    for i in range(1, len(u) - 1):
        u_new[i] = 2 * u[i] - u_old[i] + (c * dt / dx)**2 * (u[i+1] - 2*u[i] + u[i-1])
    return u_new

# Simulation parameters
L = 1.0  # Length of the string
N = 100  # Number of spatial points
c = 1.0  # Wave speed
dt = 0.01  # Time step
dx = L / (N - 1)  # Spatial step

# Initial conditions
u = np.zeros(N)
u[N//2] = 1  # Initial pulse

# Simulation loop
u_old = u.copy()
fig, ax = plt.subplots()
line, = ax.plot(np.linspace(0, L, N), u)
ax.set_ylim(-1.5, 1.5)
ax.set_xlim(0, L)

def animate(i):
    global u, u_old
    u = wave_equation(u, c, dx, dt)
    line.set_ydata(u)
    u_old = u.copy()
    return line,

ani = animation.FuncAnimation(fig, animate, frames=200, interval=10, blit=True)
plt.show()

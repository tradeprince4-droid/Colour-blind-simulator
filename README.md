# Colour-blind-simulatorM = {
    "protanopia":   [[0.567, 0.433, 0], [0.558, 0.442, 0], [0, 0.242, 0.758]],
    "deuteranopia": [[0.625, 0.375, 0], [0.7, 0.3, 0], [0, 0.3, 0.7]],
    "tritanopia":   [[0.95, 0.05, 0], [0, 0.433, 0.567], [0, 0.475, 0.525]],
}

def simulate(h, kind):
    h = h.lstrip("#")
    rgb = [int(h[i:i+2], 16) for i in (0, 2, 4)]
    out = [min(255, round(sum(m * c for m, c in zip(row, rgb)))) for row in M[kind]]
    return "#%02X%02X%02X" % tuple(out)

for k in M:
    print(k, simulate("#DA3633", k))

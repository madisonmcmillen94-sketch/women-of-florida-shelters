"""
Women of Florida Shelters — Florida DV Centers Carousel
Generates a set of square (1080x1080) PNG slides listing all 42 FCADV-certified
Florida domestic violence centers, grouped by region, plus a title slide and a
closing hotline slide. Also writes a ready-to-paste Facebook caption.

Run: python3 generate_carousel.py
Output: ./output/slide_01_title.png ... slide_NN_hotline.png, caption.txt
"""

from PIL import Image, ImageDraw, ImageFont
import os
import textwrap

# ---------- Config ----------

W, H = 1080, 1080
OUT_DIR = os.path.join(os.path.dirname(__file__), "output")
os.makedirs(OUT_DIR, exist_ok=True)

FONT_DIR = "/usr/share/fonts/truetype/dejavu"
F_BOLD = os.path.join(FONT_DIR, "DejaVuSans-Bold.ttf")
F_REG = os.path.join(FONT_DIR, "DejaVuSans.ttf")

# Warm, calm palette — approachable but credible for a resource page
BG_TOP = (91, 74, 122)      # deep plum
BG_BOTTOM = (58, 47, 92)    # darker plum
CARD_BG = (255, 255, 255)
ACCENT = (222, 163, 96)     # warm gold accent
TEXT_DARK = (43, 38, 56)
TEXT_MUTED = (110, 104, 122)
TEXT_LIGHT = (255, 255, 255)
HOTLINE_BG = (196, 90, 90)  # warm red-orange for the closing hotline slide

MARGIN = 64

# ---------- Data ----------
# (Organization, counties served)

REGIONS = {
    "Panhandle": [
        ("Favor House of Northwest Florida", "Escambia, Santa Rosa"),
        ("Shelter House, Inc.", "Okaloosa, Walton"),
        ("Salvation Army of Panama City", "Bay, Calhoun, Gulf, Holmes, Jackson, Washington"),
        ("Refuge House", "Gadsden, Franklin, Jefferson, Leon, Liberty, Madison, Taylor, Wakulla"),
    ],
    "North Central": [
        ("Another Way, Inc.", "Columbia, Dixie, Gilchrist, Hamilton, Lafayette, Levy"),
        ("Vivid Visions, Inc.", "Suwannee"),
        ("Peaceful Paths Domestic Abuse Network", "Alachua, Bradford, Union"),
        ("Ocala Domestic Violence / Sexual Assault Center", "Marion"),
    ],
    "Northeast": [
        ("Hubbard House (Spouse Abuse, Inc.)", "Baker, Duval"),
        ("Micah's Place, Inc.", "Nassau"),
        ("Quigley House, Inc.", "Clay"),
        ("Betty Griffin House (Safety Shelter of St. Johns Co.)", "St. Johns"),
        ("Lee Conlee House", "Putnam"),
        ("Beacon Center", "Volusia"),
        ("Family Life Center (Flagler Ecumenical SSC)", "Flagler"),
    ],
    "Central": [
        ("Harbor House", "Orange"),
        ("Haven of Lake and Sumter Counties", "Sumter, Lake"),
        ("Help Now of Osceola, Inc.", "Osceola"),
        ("Peace River Center DV Shelter", "Hardee, Highlands, Polk"),
    ],
    "Tampa Bay": [
        ("Community Action Stops Abuse", "Pinellas"),
        ("The Haven of RCS", "Pinellas"),
        ("DAWN Center of Hernando Co. (Salvare, Inc.)", "Hernando"),
        ("Sunrise of Pasco", "Pasco"),
        ("Salvation Army DV Program of West Pasco", "Pasco"),
        ("The Spring of Tampa Bay, Inc.", "Hillsborough"),
        ("Citrus County Abuse Shelter Assoc. (CASA)", "Citrus"),
    ],
    "Southwest": [
        ("Abuse Counseling and Treatment, Inc. (ACT)", "Glades, Hendry, Lee"),
        ("Center for Abuse and Rape Emergencies (CARE)", "Charlotte"),
        ("Safe Place and Rape Crisis Center (SPARCC)", "DeSoto, Sarasota"),
        ("Shelter for Abused Women & Children (SAWCC)", "Collier"),
    ],
    "Space & Treasure Coast": [
        ("Salvation Army Brevard County", "Brevard"),
        ("Serene Harbor", "Brevard"),
        ("SafeSpace, Inc.", "Indian River, Martin, St. Lucie"),
        ("Martha's House", "Okeechobee"),
        ("SafeHouse of Seminole", "Seminole"),
    ],
    "Southeast": [
        ("Aid to Victims of Domestic Abuse", "Palm Beach"),
        ("YWCA Harmony House of Palm Beach County", "Palm Beach"),
        ("Women In Distress of Broward County", "Broward"),
        ("HOPE Family Services, Inc.", "Manatee"),
    ],
    "South Florida": [
        ("Miami-Dade Advocates for Victims, Safespace", "North Miami-Dade"),
        ("The Lodge (Victim Response, Inc.)", "Miami-Dade"),
        ("Domestic Abuse Shelter", "Monroe"),
    ],
}

STATEWIDE_HOTLINE = "1-800-500-1119"

# ---------- Helpers ----------

def load_font(path, size):
    return ImageFont.truetype(path, size)

def vertical_gradient(w, h, top, bottom):
    base = Image.new("RGB", (w, h), top)
    draw = ImageDraw.Draw(base)
    for y in range(h):
        t = y / max(h - 1, 1)
        r = int(top[0] + (bottom[0] - top[0]) * t)
        g = int(top[1] + (bottom[1] - top[1]) * t)
        b = int(top[2] + (bottom[2] - top[2]) * t)
        draw.line([(0, y), (w, y)], fill=(r, g, b))
    return base

def wrap_text(draw, text, font, max_width):
    words = text.split()
    lines, cur = [], ""
    for word in words:
        trial = (cur + " " + word).strip()
        if draw.textlength(trial, font=font) <= max_width:
            cur = trial
        else:
            if cur:
                lines.append(cur)
            cur = word
    if cur:
        lines.append(cur)
    return lines

def footer(draw, page_no, total):
    f = load_font(F_REG, 24)
    label = "Women of Florida Shelters"
    draw.text((MARGIN, H - 56), label, font=f, fill=(255, 255, 255, 160))
    pg = f"{page_no} / {total}"
    w = draw.textlength(pg, font=f)
    draw.text((W - MARGIN - w, H - 56), pg, font=f, fill=(255, 255, 255, 160))

# ---------- Slide builders ----------

def slide_title(total_pages):
    img = vertical_gradient(W, H, BG_TOP, BG_BOTTOM)
    draw = ImageDraw.Draw(img)

    f_kicker = load_font(F_BOLD, 30)
    f_title = load_font(F_BOLD, 66)
    f_sub = load_font(F_REG, 32)

    kicker = "RESOURCE GUIDE"
    draw.text((MARGIN, 140), kicker, font=f_kicker, fill=ACCENT)

    title_lines = ["Florida's 42 Certified", "Domestic Violence", "Centers"]
    y = 200
    for line in title_lines:
        draw.text((MARGIN, y), line, font=f_title, fill=TEXT_LIGHT)
        y += 78

    sub = "Every certified center in the state, grouped by region — swipe through to find the one that covers your county."
    sub_lines = wrap_text(draw, sub, f_sub, W - 2 * MARGIN)
    y += 30
    for line in sub_lines:
        draw.text((MARGIN, y), line, font=f_sub, fill=(230, 224, 240))
        y += 42

    # accent divider
    draw.rectangle([MARGIN, y + 20, MARGIN + 120, y + 26], fill=ACCENT)

    # bottom hotline callout
    f_bh = load_font(F_BOLD, 30)
    draw.text((MARGIN, H - 160), "24/7 Statewide Hotline", font=f_bh, fill=ACCENT)
    f_bn = load_font(F_BOLD, 46)
    draw.text((MARGIN, H - 120), STATEWIDE_HOTLINE, font=f_bn, fill=TEXT_LIGHT)

    footer(draw, 1, total_pages)
    return img

def slide_region(region_name, orgs, page_no, total_pages):
    img = vertical_gradient(W, H, BG_TOP, BG_BOTTOM)
    draw = ImageDraw.Draw(img)

    f_kicker = load_font(F_BOLD, 28)
    f_region = load_font(F_BOLD, 54)
    f_org = load_font(F_BOLD, 30)
    f_county = load_font(F_REG, 24)

    draw.text((MARGIN, 70), "REGION", font=f_kicker, fill=ACCENT)
    draw.text((MARGIN, 106), region_name, font=f_region, fill=TEXT_LIGHT)
    draw.rectangle([MARGIN, 178, MARGIN + 90, 184], fill=ACCENT)

    card_top = 220
    card_bottom = H - 100
    draw.rounded_rectangle([MARGIN - 24, card_top, W - MARGIN + 24, card_bottom],
                            radius=28, fill=CARD_BG)

    inner_w = (W - MARGIN + 24) - (MARGIN - 24) - 64
    y = card_top + 40
    x = MARGIN

    for i, (name, counties) in enumerate(orgs):
        name_lines = wrap_text(draw, name, f_org, inner_w)
        for line in name_lines:
            draw.text((x, y), line, font=f_org, fill=TEXT_DARK)
            y += 38
        county_lines = wrap_text(draw, f"Counties: {counties}", f_county, inner_w)
        for line in county_lines:
            draw.text((x, y), line, font=f_county, fill=TEXT_MUTED)
            y += 30
        y += 22
        if i < len(orgs) - 1:
            draw.line([(x, y - 10), (x + inner_w, y - 10)], fill=(230, 226, 236), width=2)
            y += 6

    footer(draw, page_no, total_pages)
    return img

def slide_hotline(total_pages):
    img = Image.new("RGB", (W, H), HOTLINE_BG)
    draw = ImageDraw.Draw(img)

    f_kicker = load_font(F_BOLD, 30)
    f_num = load_font(F_BOLD, 84)
    f_body = load_font(F_REG, 32)
    f_small = load_font(F_REG, 26)

    draw.text((MARGIN, 180), "NOT SURE WHICH CENTER TO CALL?", font=f_kicker, fill=(255, 236, 214))

    y = 240
    draw.text((MARGIN, y), "Florida Domestic", font=load_font(F_BOLD, 50), fill=TEXT_LIGHT)
    y += 62
    draw.text((MARGIN, y), "Violence Hotline", font=load_font(F_BOLD, 50), fill=TEXT_LIGHT)
    y += 90

    draw.text((MARGIN, y), STATEWIDE_HOTLINE, font=f_num, fill=(255, 255, 255))
    y += 120

    body = "Available 24/7. Advocates connect you to the certified center that covers your county and can talk through shelter, safety planning, and next steps."
    for line in wrap_text(draw, body, f_body, W - 2 * MARGIN):
        draw.text((MARGIN, y), line, font=f_body, fill=(255, 236, 220))
        y += 42

    y += 30
    draw.text((MARGIN, y), "TDD: 1-800-621-4202", font=f_small, fill=(255, 236, 220))
    y += 34
    draw.text((MARGIN, y), "fcadv.org/centers — full directory", font=f_small, fill=(255, 236, 220))

    footer(draw, total_pages, total_pages)
    return img

# ---------- Build ----------

def main():
    region_items = list(REGIONS.items())
    total_pages = 1 + len(region_items) + 1  # title + regions + hotline

    page = 1
    slide_title(total_pages).save(os.path.join(OUT_DIR, f"slide_{page:02d}_title.png"))

    for region_name, orgs in region_items:
        page += 1
        safe_name = region_name.lower().replace(" ", "_").replace("&", "and")
        slide_region(region_name, orgs, page, total_pages).save(
            os.path.join(OUT_DIR, f"slide_{page:02d}_{safe_name}.png")
        )

    page += 1
    slide_hotline(total_pages).save(os.path.join(OUT_DIR, f"slide_{page:02d}_hotline.png"))

    caption = """Florida has 42 certified domestic violence centers, and every single county is covered by one. 📍

Swipe through for the full list, grouped by region, with the counties each center serves. Bookmark this post — you never know when you or someone you love will need it.

Not sure which one covers your county? Call the Florida Domestic Violence Hotline, 24/7: 1-800-500-1119. TDD: 1-800-621-4202.

Full directory: fcadv.org/centers

#WomenOfFloridaShelters #DomesticViolenceAwareness #FloridaResources #DVSupport #SafetyPlanning #YouAreNotAlone"""

    with open(os.path.join(OUT_DIR, "caption.txt"), "w") as f:
        f.write(caption)

    print(f"Generated {page} slides + caption.txt in {OUT_DIR}")

if __name__ == "__main__":
    main()

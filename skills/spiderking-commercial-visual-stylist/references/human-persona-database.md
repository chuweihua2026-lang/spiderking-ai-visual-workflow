# AI Fashion Human Persona Database V1.0

## Purpose

Act as an international consumer-insight specialist and commercial advertising director. Select the person who gives the target consumer the strongest credible identification with the product and its ideal lifestyle. Do not simply select the youngest or most attractive person.

## Selection Chain

Select in this order:

1. Product category and credible function.
2. Product price band: mass, mid, or premium.
3. Target consumer.
4. Purchase decision-maker.
5. Actual user.
6. Use scene and lifestyle.
7. Persona ID.

Examples:

- Premium men's leather shoes should usually use a credible 35-50-year-old professional or business leader rather than an 18-year-old fashion model.
- Children's luggage should show the child user and, when commercially useful, the parent decision-maker.
- Women's premium bags should distinguish young, urban professional, and mature consumers according to price, design, and use context.

## Male Personas

| ID | Persona | Age | Identity | Motivation | Styling | Suitable products | Scenes |
|---|---|---:|---|---|---|---|---|
| M01 | Successful Business Man | 38-50 | owner, executive, business professional; mid-high income | quality, status, reliability | suit, shirt, coat, leather shoes, mechanical watch | business leather shoes, briefcases, premium leather goods | office, hotel, business district |
| M02 | Urban White-Collar Man | 28-38 | finance, technology, design, corporate employee | comfort, quality, efficiency | casual tailoring, knitwear, casual trousers | casual leather shoes, business-sport hybrid shoes | cafe, office, contemporary workspace |
| M03 | Young Trend Man | 18-30 | student, young employee, freelancer | individuality, trends, social display | sweatshirt, denim, sportswear | sneakers, trend footwear | campus, street, youth district |
| M04 | Outdoor Explorer Man | 30-55 | entrepreneur, outdoor enthusiast, photographer | freedom, health, experience | shell jacket, utility trousers, outdoor shoes | outdoor footwear, travel equipment | mountains, forest, travel route |

## Female Personas

| ID | Persona | Age | Identity | Motivation | Styling | Suitable products | Scenes |
|---|---|---:|---|---|---|---|---|
| F01 | Youthful Young Woman | 18-25 | university student, early-career employee | appearance, trends, social expression | denim, knitwear, sports-casual pieces; skirts only when product function supports them | small bags, sneakers, youthful footwear | campus, cafe, city street |
| F02 | Refined Urban Woman | 25-35 | professional, designer, brand sales | quality, aesthetics, self-expression | trench coat, tailoring, dress, refined separates | women's bags, premium fashion footwear | commercial street, art space |
| F03 | Mature Elegant Woman | 35-50 | executive, household decision-maker, senior professional | quality, classic value, durability | cashmere, silk, coat, refined tailoring | premium leather goods, women's footwear | premium hotel, gallery, cultural venue |
| F04 | Urban Mother | 30-45 | family consumer and household decision-maker | practicality, quality, family needs | comfortable, clean, understated outfits | functional bags, casual shoes, luggage | shopping mall, family space, family travel |

## Family Personas

| ID | Persona | People | Need | Motivation | Scenes |
|---|---|---|---|---|---|
| H01 | Back-to-School Family | mother 35-45 and child 7-18 | school supplies, luggage, footwear and apparel | give the child a better start | campus, mall, home preparation |
| H02 | Family Travel Group | parents 30-45 and child 5-15 | luggage, outdoor and travel products | convenient, enjoyable family travel | airport, station, travel destination |

## Occupational Cross-Check

- Business Owner, 40-55: successful, decisive, quality-led; premium leather shoes and business bags.
- Corporate Manager, 35-45: professional, reliable; business footwear and commuter bags.
- Young Employee, 25-35: growth, efficiency; casual and commuter footwear.
- Student, 15-22: youth, future; sports footwear and campus luggage.
- Traveler, 25-60: exploration, freedom; luggage and outdoor footwear.

Use occupation as a consistency check, not as a substitute for the full persona selection chain.

## Purchasing-Power Models

- Mass: price, practicality, value, and credible daily use; ordinary employees and family users.
- Mid: quality, brand, and experience; urban professionals and young families.
- Premium: identity, design, materials, and scarcity; owners, executives, and high-income professionals.

Do not invent an exact product price. If price is unknown, infer a tentative band from supplied positioning and visible construction, label it as an inference, and avoid overstating status.

## Temperament Vocabulary

- Business: mature, steady, professional, trustworthy.
- Young: sunny, energetic, trend-aware.
- Women Fashion: elegant, refined, confident.
- Outdoor: healthy, free, exploratory.
- Family: warm, happy, reassuring.

## Action Library

- Business footwear: purposeful walking, adjusting a cuff, entering an office building.
- Sports footwear: athletic stance, campus walking, movement-ready posture.
- Women's bag: hand carry, shoulder carry, controlled glance-back.
- Luggage: pulling luggage, airport walking, hotel arrival.
- Outdoor footwear: stable footing on a trail, one foot on a low rock or step, map or route-check gesture, standing rest at a viewpoint.

Downstream campaign rules override incompatible actions. For example, if the SpiderKing Styling Engine requires standing models, do not select sitting or full running actions. Product visibility and physical plausibility always take priority.

## Extension Rule

The database is a selection foundation, not a cage. When no standard persona fits, create an `EXT-*` persona with the same fields: age, gender, occupation, family status, purchasing power, consumer motivation, clothing language, temperament, products, and scenes. Record the closest standard persona and the reason for extension.

## Persona Audit

Before generation, answer and pass all six checks:

1. Is this person a credible real consumer, user, or purchase decision-maker for the product?
2. Does the age match the product, price band, and lifestyle?
3. Is the occupation or family identity plausible?
4. Does the clothing fit that identity and the product function?
5. Does the scene fit the person's real lifestyle?
6. Does the person increase the product's perceived value and consumer identification?

If any answer is no, set the commercial styling decision to `needs_revision` and do not generate.

Final principle: commercial advertising does not merely display a model. It presents the consumer's credible ideal life.

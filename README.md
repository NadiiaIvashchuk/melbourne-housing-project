# melbourne-housing-project

This is a snapshot of a dataset created by Tony Pino.

It was scraped from publicly available results posted every week from Domain.com.au. He cleaned it well, and now it's up to you to make data analysis magic. The dataset includes Address, Type of Real estate, Suburb, Method of Selling, Rooms, Price, Real Estate Agent, Date of Sale and distance from C.B.D.

Notes on Specific Variables
- Rooms: Number of rooms
- Price: Price in dollars
- Method: S - property sold; SP - property sold prior; PI - property passed in; PN - sold prior not disclosed; SN - sold not disclosed; NB - no bid; VB - vendor bid; W - withdrawn prior to auction; SA - sold after auction; SS - sold after auction price not disclosed. N/A - price or highest bid not available.
- Type: br - bedroom(s); h - house,cottage,villa, semi,terrace; u - unit, duplex; t - townhouse; dev site - development site; o res - other residential.
- SellerG: Real Estate Agent
- Date: Date sold
- Distance: Distance from CBD
- Regionname: General Region (West, North West, North, North east …etc)
- Propertycount: Number of properties that exist in the suburb.
- Bedroom2 : Scraped # of Bedrooms (from different source)
- Bathroom: Number of Bathrooms
- Car: Number of carspots
- Landsize: Land Size
- BuildingArea: Building Size
- CouncilArea: Governing council for the area  

## Goal our project  

Full cycle of data analyst work:
cleaning -> EDA -> Feature engineering -> Model -> Predict -> Conclusions

## Датасет

- Name: **Melbourne Housing Snapshot**
- Source (Kaggle): `https://www.kaggle.com/datasets/dansbecker/melbourne-housing-snapshot`
- File: `melb_data.csv`
- Target: column `Price` (sell price).

Короткий зміст стовпців: характеристики об'єкта (кількість кімнат `Rooms`, тип житла `Type`, відстань до центру `Distance`, площа ділянки `Landsize`, рік побудови `YearBuilt`, координати тощо), а також район (`Suburb`, `Regionname`, `CouncilArea`), спосіб і дата продажу (`Method`, `Date`)

### Before cleaning and EDA:  
- Data set has 13580 rows, 21 columns
- Columns with null data: 




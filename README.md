---
title: Rails Starter
description: A Rails starter app using a PostgreSQL database
tags:
  - ruby
  - rails
  - postgresql
---

# Rails Starter Example

This is a [Ruby on Rails](https://rubyonrails.org/) starter app that connects to a Railway Postgres database and supports [Action Cable](https://guides.rubyonrails.org/action_cable_overview.html).

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template/sibk1f)

## ✨ Features

- Ruby
- Rails
- Postgres
- Redis

## 💁‍♀️ How to use

- [Create a Railway project with the Postgres plugin](https://railway.app/project?plugins=postgresql)
- Connect to your Railway project with `railway link`
- Install Ruby requirements `bundle install`
- Migrate the database `railway run rake db:migrate`
- Run Rails `railway run bin/rails server`

## 📝 Notes

This app was generated with the `rails new` command. Read more about Rails on
their [official website](https://rubyonrails.org/)ok


import requests
import json

def fetch_earthquake_data():
    # USGS API for past day's all earthquake data
    url = "https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_day.geojson"
    
    # Send a HTTP request to the URL
    response = requests.get(url)
    
    # If request is successful, status code will be 200
    if response.status_code == 200:
        # Get the content of the response
        data = response.content
        
        # Parse JSON data
        earthquakes = json.loads(data)
        
        # Print earthquake data
        for earthquake in earthquakes["features"]:
            print(f"Magnitude: {earthquake['properties']['mag']}, Location: {earthquake['properties']['place']}")
    else:
        print(f"Failed to fetch earthquake data, status code: {response.status_code}")

fetch_earthquake_data()

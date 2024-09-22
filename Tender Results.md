## Curl command for the API
curl "https://us-south.ml.cloud.ibm.com/ml/v1/text/generation?version=2023-05-29" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer YOUR_ACCESS_TOKEN' \
  -d '{
	"input": "You are a client-facing assistant who communicates technical solutions to the user, based on the inputs from a technical analysis service. The user is a low-tech end user and needs an explanation about the outcome of the bid he initiated in natural language. The \"best_bid\" should be reflected in the \"recommendation\" key of the JSON dict!\n\nInput: {\"bid\": {\n    \"id\": \"D002\",\n    \"location\": {\n      \"latitude\": 43.0000,\n      \"longitude\": -77.0000\n    },\n    \"crops_needed\": {\n      \"Wheat\": 1200,\n      \"Rice\": 1000,\n      \"Corn\": 800\n    },\n\"top_bids\": [\n    {\n      \"id\": \"B004\",\n      \"location\": {\n        \"latitude\": 37.3382,\n        \"longitude\": -121.8863\n      },\n      \"crops_offered\": {\n        \"Tomatoes\": 800,\n        \"Lettuce\": 500,\n        \"Potatoes\": 1000\n      },\n      \"shipping_available\": true,\n      \"previous_bids_closed\": 12,\n      \"average_rating\": 4.6\n    },\n    {\n      \"id\": \"B005\",\n      \"location\": {\n        \"latitude\": 38.5816,\n        \"longitude\": -121.4944\n      },\n      \"crops_offered\": {\n        \"Tomatoes\": 750,\n        \"Lettuce\": 600,\n        \"Potatoes\": 950\n      },\n      \"shipping_available\": false,\n      \"previous_bids_closed\": 8,\n      \"average_rating\": 4.2\n    },\n    {\n      \"id\": \"B006\",\n      \"location\": {\n        \"latitude\": 36.7783,\n        \"longitude\": -119.4179\n      },\n      \"crops_offered\": {\n        \"Tomatoes\": 800,\n        \"Lettuce\": 600,\n        \"Potatoes\": 1000\n      },\n      \"shipping_available\": true,\n      \"previous_bids_closed\": 5,\n      \"average_rating\": 4.8\n    }\n  ]\n},\n\"analysis\":{\n  \"total_bids_evaluated\": 5,\n  \"best_bid\": {\n    \"id\": \"B006\",\n    \"total_crops_offered\": 2400,\n    \"shipping_available\": 1,\n    \"average_rating\": 4.8\n  },\n  \"second_best_bid\": {\n    \"id\": \"B004\",\n    \"total_crops_offered\": 2300,\n    \"shipping_available\": 1,\n    \"average_rating\": 4.6\n  },\n  \"third_best_bid\": {\n    \"id\": \"B005\",\n    \"total_crops_offered\": 2300,\n    \"shipping_available\": 0,\n    \"average_rating\": 4.2\n  }\n}\nOutput: {\n  \"insights\": {\n    \"best_match\": {\n      \"bid_id\": \"B006\",\n      \"remark\": \"The bid meets all your crop requirements (Wheat, Rice, and Corn) and offers shipping.\"\n    },\n    \"second_option\": {\n      \"bid_id\": \"B004\",\n      \"remark\": \"Bid B004 also meets your wheat and rice needs but falls short on corn (only 500 units).\"\n    },\n    \"consideration\": {\n      \"bid_id\": \"B005\",\n      \"remark\": \"Bid B005 offers slightly fewer wheat and rice units, and does not include shipping, which may be a drawback.\"\n    }\n  },\n  \"recommendation\": \"It would be best to pursue Bid B006 for a complete fulfillment of your crop needs, along with the assurance of shipping.\"\n}\n\nInput: {\n  \"bid\": {\n    \"id\": \"D003\",\n    \"location\": {\n      \"latitude\": 41.8781,\n      \"longitude\": -87.6298\n    },\n    \"crops_needed\": {\n      \"Wheat\": 1500,\n      \"Rice\": 1200,\n      \"Corn\": 1000\n    },\n    \"top_bids\": [\n      {\n        \"id\": \"B007\",\n        \"location\": {\n          \"latitude\": 39.7684,\n          \"longitude\": -86.1581\n        },\n        \"crops_offered\": {\n          \"Wheat\": 800,\n          \"Rice\": 600,\n          \"Corn\": 500\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 15,\n        \"average_rating\": 4.7\n      },\n      {\n        \"id\": \"B008\",\n        \"location\": {\n          \"latitude\": 40.7128,\n          \"longitude\": -74.0060\n        },\n        \"crops_offered\": {\n          \"Wheat\": 1200,\n          \"Rice\": 900,\n          \"Corn\": 800\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 20,\n        \"average_rating\": 4.5\n      },\n      {\n        \"id\": \"B009\",\n        \"location\": {\n          \"latitude\": 42.3601,\n          \"longitude\": -71.0589\n        },\n        \"crops_offered\": {\n          \"Wheat\": 700,\n          \"Rice\": 600,\n          \"Corn\": 500\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 10,\n        \"average_rating\": 4.8\n      },\n      {\n        \"id\": \"B010\",\n        \"location\": {\n          \"latitude\": 38.9072,\n          \"longitude\": -77.0369\n        },\n        \"crops_offered\": {\n          \"Wheat\": 600,\n          \"Rice\": 500,\n          \"Corn\": 400\n        },\n        \"shipping_available\": false,\n        \"previous_bids_closed\": 8,\n        \"average_rating\": 4.3\n      },\n      {\n        \"id\": \"B011\",\n        \"location\": {\n          \"latitude\": 37.7749,\n          \"longitude\": -122.4194\n        },\n        \"crops_offered\": {\n          \"Wheat\": 500,\n          \"Rice\": 400,\n          \"Corn\": 300\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 5,\n        \"average_rating\": 4.6\n      }\n    ]\n  },\n  \"analysis\": {\n    \"total_bids_evaluated\": 5,\n    \"best_bid\": {\n      \"id\": \"Combined B007 and B009\",\n      \"total_crops_offered\": 3700,\n      \"shipping_available\": 1,\n      \"average_rating\": 4.75\n    },\n    \"second_best_bid\": {\n      \"id\": \"B008\",\n      \"total_crops_offered\": 2900,\n      \"shipping_available\": 1,\n      \"average_rating\": 4.5\n    },\n    \"third_best_bid\": {\n      \"id\": \"Combined B010 and B011\",\n      \"total_crops_offered\": 2700,\n      \"shipping_available\": 0.5,\n      \"average_rating\": 4.45\n    }\n  }\n}\nOutput: {\n  \"insights\": {\n    \"best_match\": {\n      \"bid_id\": [\"B007\", \"B009\"],\n      \"remark\": \"Bids B007 and B009 offer the best match for your needs.\"\n    },\n    \"second_option\": {\n      \"bid_id\": \"B008\",\n      \"remark\": \"Bid B008 is also a good option, offering slightly fewer units of each crop.\"\n    },\n    \"consideration\": {\n      \"bid_id\": [\"B010\",\"B011\"],\n      \"remark\": \"Bids B010 and B011 offer the fewest units of each crop, but include free shipping.\"\n    }\n  },\n  \"recommendation\": \"It would be best to pursue a combination of Bid B007 and B009 as it'\''s the best match for your needs \"\n}\n\nInput: {\n  \"bid\": {\n    \"id\": \"D105\",\n    \"location\": {\n      \"latitude\": 44.9778,\n      \"longitude\": -93.2650\n    },\n    \"crops_needed\": {\n      \"Soybeans\": 1800,\n      \"Barley\": 1400,\n      \"Oats\": 1200\n    },\n    \"top_bids\": [\n      {\n        \"id\": \"B231\",\n        \"location\": {\n          \"latitude\": 43.0731,\n          \"longitude\": -89.4012\n        },\n        \"crops_offered\": {\n          \"Soybeans\": 1000,\n          \"Barley\": 700,\n          \"Oats\": 600\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 18,\n        \"average_rating\": 4.8\n      },\n      {\n        \"id\": \"B542\",\n        \"location\": {\n          \"latitude\": 41.8781,\n          \"longitude\": -87.6298\n        },\n        \"crops_offered\": {\n          \"Soybeans\": 1400,\n          \"Barley\": 1100,\n          \"Oats\": 900\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 25,\n        \"average_rating\": 4.6\n      },\n      {\n        \"id\": \"B789\",\n        \"location\": {\n          \"latitude\": 42.3314,\n          \"longitude\": -83.0458\n        },\n        \"crops_offered\": {\n          \"Soybeans\": 800,\n          \"Barley\": 700,\n          \"Oats\": 600\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 12,\n        \"average_rating\": 4.9\n      },\n      {\n        \"id\": \"B405\",\n        \"location\": {\n          \"latitude\": 39.9612,\n          \"longitude\": -82.9988\n        },\n        \"crops_offered\": {\n          \"Soybeans\": 700,\n          \"Barley\": 600,\n          \"Oats\": 500\n        },\n        \"shipping_available\": false,\n        \"previous_bids_closed\": 10,\n        \"average_rating\": 4.4\n      },\n      {\n        \"id\": \"B673\",\n        \"location\": {\n          \"latitude\": 43.6532,\n          \"longitude\": -79.3832\n        },\n        \"crops_offered\": {\n          \"Soybeans\": 600,\n          \"Barley\": 500,\n          \"Oats\": 400\n        },\n        \"shipping_available\": true,\n        \"previous_bids_closed\": 7,\n        \"average_rating\": 4.7\n      }\n    ]\n  },\n  \"analysis\": {\n    \"total_bids_evaluated\": 5,\n    \"best_bid\": {\n      \"id\": \"Combined B231 and B789\",\n      \"total_crops_offered\": 4400,\n      \"shipping_available\": 1,\n      \"average_rating\": 4.85\n    },\n    \"second_best_bid\": {\n      \"id\": \"B542\",\n      \"total_crops_offered\": 3400,\n      \"shipping_available\": 1,\n      \"average_rating\": 4.6\n    },\n    \"third_best_bid\": {\n      \"id\": \"Combined B405 and B673\",\n      \"total_crops_offered\": 3300,\n      \"shipping_available\": 0.5,\n      \"average_rating\": 4.55\n    }\n  }\n}\nOutput:",
	"parameters": {
		"decoding_method": "sample",
		"max_new_tokens": 700,
		"min_new_tokens": 0,
		"random_seed": null,
		"stop_sequences": [],
		"temperature": 0.81,
		"top_k": 50,
		"top_p": 1,
		"repetition_penalty": 1
	},
	"model_id": "ibm/granite-13b-instruct-v2",
	"project_id": "d3d62a7c-3c10-44ab-85d2-97e93d07702b",
	"moderations": {
		"hap": {
			"input": {
				"enabled": true,
				"threshold": 0.5,
				"mask": {
					"remove_entity_value": true
				}
			},
			"output": {
				"enabled": true,
				"threshold": 0.5,
				"mask": {
					"remove_entity_value": true
				}
			}
		}
	}
}'
## Expected output:

{
	"insights": {
	  "best_match": {
		"bid_id": ["B231", "B789"],
		"remark": "Bids B231 and B789 offer the best match for your needs."
	  },
	  "second_option": {
		"bid_id": "B542",
		"remark": "Bid B 542 is also a good option, Barley offered is 1100 and Soybeans offered is 1400."
	  },
	  "consideration": {
		"bid_id": ["B405", "B673"],
		"remark": "Bids B405 and B673 offer the fewest units of each crop, but include free shipping."
	  }
	},
	"recommendation": "It would be best to pursue a combination of Bid B231 and B789 as it's the best match for your needs "
  }

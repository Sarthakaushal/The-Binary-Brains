## Curl command for the API
{
	"input": "Analyse bids by users to create a comparative evaluation & provide analysis in natural language based on the guidelines provided below\n//Guidelines//\nYou are a judge in comparing bids of different farmers that are bidding for contracts on online contracts, the rules that you need to keep in mind are based on 5 pillars, each ranked in decreasing order of priority, also generate insights on how a particular bid could improve its relative position, and give a quantitative measure on the %age improvement in the rank:\n\n1. Bid fulfills all the crops required in required quantities\n2. If a bidder is able to provide shipping then he is preferred over a bidder that doesn't 3. provide shipping\n3. A bidder closer to the distributor is preferred: based on the distance via lat-long of each farmer and distributor\n4. Number of previously closed bids\n5. Reviews of distributors from previous bids\n\nProvide the analysis separately as a JSON and the insight in very careful way that looks like a suggestion to improve Customer Experience!!\nGiven the data below in JSON format, provide the output in JSON only!!\n\nInput: // Distributor Data//\n{{\n  \"distributor\": {\n    \"id\": \"D001\",\n    \"location\": {\n      \"latitude\": 42.9634,\n      \"longitude\": -78.7474\n    },\n    \"required_crops\": {\n      \"Wheat\": 1000,\n      \"Rice\": 500,\n      \"Corn\": 300\n    }\n  }\n}\n// Bids//\n{\n  \"bidders\": [\n    {\n      \"id\": \"B001\",\n      \"location\": {\n        \"latitude\": 42.8854,\n        \"longitude\": -78.8784\n      },\n      \"crops_offered\": {\n        \"Wheat\": 800,\n        \"Rice\": 500,\n        \"Corn\": 300\n      },\n      \"shipping_available\": true,\n      \"previous_bids_closed\": 15,\n      \"average_rating\": 4.5,\n    },\n    {\n      \"id\": \"B002\",\n      \"location\": {\n        \"latitude\": 42.6526,\n        \"longitude\": -73.7562\n      },\n      \"crops_offered\": {\n        \"Wheat\": 1000,\n        \"Rice\": 450,\n        \"Corn\": 300\n      },\n      \"shipping_available\": false,\n      \"previous_bids_closed\": 20,\n      \"average_rating\": 4.0,\n    },\n    {\n      \"id\": \"B003\",\n      \"location\": {\n        \"latitude\": 42.7302,\n        \"longitude\": -73.6918\n      },\n      \"crops_offered\": {\n        \"Wheat\": 1000,\n        \"Rice\": 500,\n        \"Corn\": 300\n      },\n      \"shipping_available\": true,\n      \"previous_bids_closed\": 10,\n      \"average_rating\": 4.7,\n    }\n  ]\n}\nOutput: {\n   \"evaluation\": {\n    \"B001\": {\n      \"pillar_scores\": {\n        \"crop_fulfillment\": 86,\n        \"shipping_availability\": 100,\n        \"proximity\": 90,\n        \"closed_bids\": 75,\n        \"reviews\": 90\n      },\n      \"total_score\": 90.4,\n      \"improvement_suggestions\": {\n        \"crop_fulfillment\": \"Increase wheat supply to match the required 1000 kg to improve fulfillment score.\"\n      },\n      \"potential_improvement\": 95.4\n    },\n    \"B002\": {\n      \"pillar_scores\": {\n        \"crop_fulfillment\": 96,\n        \"shipping_availability\": 0,\n        \"proximity\": 50,\n        \"closed_bids\": 100,\n        \"reviews\": 80\n      },\n      \"total_score\": 53.9,\n      \"improvement_suggestions\": {\n        \"shipping_availability\": \"Consider providing shipping services to improve customer experience and score.\"\n      },\n      \"potential_improvement\": 80.5\n    },\n    \"B003\": {\n      \"pillar_scores\": {\n        \"crop_fulfillment\": 100,\n        \"shipping_availability\": 100,\n        \"proximity\": 65,\n        \"closed_bids\": 50,\n        \"reviews\": 95\n      },\n      \"total_score\": 86.75,\n      \"improvement_suggestions\": {\n        \"closed_bids\": \"Participate in more bids to build experience and enhance your reliability score.\"\n      },\n      \"potential_improvement\": 91.75\n    }\n  },\n\"insights\": [\n    {\n      \"bidder_id\": \"B001\",\n      \"suggestion\": \"To improve your chances of securing the contract, consider increasing the quantity of wheat offered to match the distributor's requirement of 1000 kg. This will fulfill the requirement fully and enhance your bid's competitiveness.\"\n    },\n    {\n      \"bidder_id\": \"B002\",\n      \"suggestion\": \"Adding shipping services could significantly enhance your bid's attractiveness. Offering shipping can resolve logistical issues and improve your customer satisfaction, making your bid more competitive in future contracts.\"\n    },\n    {\n      \"bidder_id\": \"B003\",\n      \"suggestion\": \"Participating in more bids can improve your reliability score and attract more distributors. With your high ratings and fulfillment of all requirements, increasing your experience will strengthen your bid's position.\"\n    }\n  ]\n}\n\nInput: //Distributor Data//\n{\n  \"distributor\": {\n    \"id\": \"D002\",\n    \"location\": {\n      \"latitude\": 37.7749,\n      \"longitude\": -122.4194\n    },\n    \"required_crops\": {\n      \"Tomatoes\": 800,\n      \"Lettuce\": 600,\n      \"Potatoes\": 1000\n    }\n  }\n}\n//Bids//\n{\n  \"bidders\": [\n    {\n      \"id\": \"B004\",\n      \"location\": {\n        \"latitude\": 37.3382,\n        \"longitude\": -121.8863\n      },\n      \"crops_offered\": {\n        \"Tomatoes\": 800,\n        \"Lettuce\": 500,\n        \"Potatoes\": 1000\n      },\n      \"shipping_available\": true,\n      \"previous_bids_closed\": 12,\n      \"average_rating\": 4.6\n    },\n    {\n      \"id\": \"B005\",\n      \"location\": {\n        \"latitude\": 38.5816,\n        \"longitude\": -121.4944\n      },\n      \"crops_offered\": {\n        \"Tomatoes\": 750,\n        \"Lettuce\": 600,\n        \"Potatoes\": 950\n      },\n      \"shipping_available\": false,\n      \"previous_bids_closed\": 8,\n      \"average_rating\": 4.2\n    },\n    {\n      \"id\": \"B006\",\n      \"location\": {\n        \"latitude\": 36.7783,\n        \"longitude\": -119.4179\n      },\n      \"crops_offered\": {\n        \"Tomatoes\": 800,\n        \"Lettuce\": 600,\n        \"Potatoes\": 1000\n      },\n      \"shipping_available\": true,\n      \"previous_bids_closed\": 5,\n      \"average_rating\": 4.8\n    }\n  ]\n}\n\nOutput:",
	"parameters": {
		"decoding_method": "greedy",
		"max_new_tokens": 1000,
		"min_new_tokens": 0,
		"stop_sequences": [],
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
}

## Expected Output
{
   "evaluation": {
    "B004": {
      "pillar_scores": {
        "crop_fulfillment": 80,
        "shipping_availability": 100,
        "proximity": 70,
        "closed_bids": 60,
         "reviews": 80
      },
      "total_score": 62.8,
      "improvement_suggestions": {
        "crop_fulfillment": "Increase the quantity of potatoes offered to match the distributor's requirement of 1000 kg to improve fulfillment score."
      },
      "potential_improvement": 70.8
    },
    "B005": {
      "pillar_scores": {
        "crop_fulfillment": 80,
        "shipping_availability": 0,
        "proximity": 50,
         "closed_bids": 80,
         "reviews": 70
      },
      "total_score": 43.2,
      "improvement_suggestions": {
        "shipping_availability": "Consider providing shipping services to improve customer experience and score."
      },
      "potential_improvement": 63.2
    },
    "B006": {
      "pillar_scores": {
        "crop_fulfillment": 80,
        "shipping_availability": 100,
         "proximity": 70,
         "closed_bids": 50,
         "reviews": 90
      },
      "total_score": 64.8,
      "improvement_suggestions": {
        "closed_bids": "Participate in more bids to build experience and enhance your reliability score."
      },
      "potential_improvement": 71.8
    }
  },
"insights": [
    {
      "bidder_id": "B004",
      "suggestion": "To improve your chances of securing the contract, consider increasing the quantity of potatoes offered to match the distributor's requirement of 1000 kg. This will fulfill the requirement fully and enhance your bid's competitiveness."
    },
    {
      "bidder_id": "B005",
      "suggestion": "Adding shipping services could significantly enhance your bid's attractiveness. Offering shipping can resolve logistical issues and improve your customer satisfaction, making your bid more competitive in future contracts."
    },
    {
      "bidder_id": "B006",
      "suggestion": "Participating in more bids can improve your reliability score and attract more distributors. With your high ratings and fulfillment of all requirements, increasing your experience will strengthen your bid's position."
    }
  ]
}

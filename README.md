# LipstickExpert
A web search engine related to lipsticks recommendation. Try it on https://lipstickexpert.netlify.app/

# Script Folder
This folder contains scripts for data processing and generating final results.

## Create environment
```bash
pip install -r requirements.txt
```


# Create Database
## Get all video_id
```bash
python get_video_id.py
```
You can change `query_list` in the main of `get_video_id.py` to get different video_id. And we get `video_id.txt`.


## Get video infomation
### please download the dataset used for sentiment analysis training at first.
```bash
tar -xvzf posdata.tar.gz
rm -rf posdata.tar.gz
tar -xvzf negdata.tar.gz
rm -rf negdata.tar.gz
```

### How to get video infomation
Please name all your video_id data with the format like  `video_{num}.txt`. One video_id dataset should contain no more than **100** video_id to avoid data loss. Result data for each dataset would be restored in `data_{num}.json`.
You can run `get_video_info.py` like this:
```bash
python get_video_info.py num
```
After you get all `.json`, you can merge all these json files by comment the parts in "__main__" that are not commented, and uncomment the parts that are commented, and then run:
```bash
python get_video_info.py
```

### Database
After the first phrase of data collection, you could get database named `video_info_database.json`.

## Get product information
First of all, we store the all color information we collected before in `color.json`, you should guarantee that `color.json` in the same folder of `get_db.py`. Besides, you need the database you get from the last step, if you database named `video_info_database.json`, you can just run the code like.
```bash
python get_db.py video_info_database.json
```
### Database
After running this python file, you could get database with both video and product information named `database_with_sephora.json`

## Train and calculate score
After we get the final json file, we rename it as final.json with sephora data inside, we run:
```bash
python scoring.py
```
The function will read in the json file and otuput a processed json file "score_list.json" with scoring infomation inside which is needed by UI part.

# User-interface folder
This folder contains the user interface implementation.
# Lipstick Recommendation Engine
![image](https://github.com/ennis-chen/EECS486/assets/113436234/ba132fee-cf15-42d6-9c73-052a9e8c440c)

## Project Overview

The Lipstick Recommendation Engine is a React-based web application designed to simplify the decision-making process for consumers in the rapidly expanding lipstick market. This project leverages data-driven insights from YouTube, utilizing a combination of metrics to recommend the top lipstick choices to users.

### Current Problem

- **Market Diversity:** The cosmetic industry, particularly the lipstick segment, has seen a substantial increase in product diversity, presenting consumers with numerous options.
- **Decision Paralysis:** This abundance creates a challenge, leading to overwhelm and uncertainty about the most suitable choices.
- **Information Overload:** Consumers face difficulties due to conflicting information from various online sources, making it hard to make well-informed decisions.

### Proposed Solution

- **Data-Driven Insights:** Our model identifies the ten most sought-after lipstick types by analyzing key metrics from highly viewed YouTube lipstick recommendation videos.
- **Robust Scoring System:** It considers factors such as the frequency of mentions, popularity metrics (likes and subscriber counts), and sentiment analysis of comments to determine product scores.
- **User-Centric Approach:** The platform enables users to refine search criteria using filters like price, benefits, and color preferences, helping them find the best lipsticks.

### Search Engine

- **ReactJS Interface:** Developed using ReactJS, offering a dynamic and responsive user experience.
- **Advanced Filtering:** Users can effortlessly sort and filter lipsticks based on their specific preferences, guided by a scoring system that ranks lipsticks based on their popularity and user feedback.
<table>
  <tr>
    <td>
      <img src="https://github.com/ennis-chen/EECS486/assets/113436234/6ecae488-724c-4a39-9d03-d5102fa4c98f" alt="image 1" style="width: 100%;">
    </td>
    <td>
      <img src="https://github.com/ennis-chen/EECS486/assets/113436234/29c281b2-2ff3-4279-ba62-7e7dc3d420ca" alt="image 2" style="width: 100%;">
    </td>
    <td>
      <img src="https://github.com/ennis-chen/EECS486/assets/113436234/7587547b-ff74-4ef2-b95e-9eae64b574fd" alt="image 3" style="width: 100%;">
    </td>
  </tr>
</table>




## Getting Started

### Prerequisites

- Node.js
- npm or yarn

### Installing

Clone the repository to your local machine:

```bash
git clone https://github.com/ennis-chen/EECS486.git
cd lipstick-recommendation-engine
git checkout ui
```


## Installation

Then, install the required packages:

```bash
npm install
```

Run with
```bash
npm start
```

You can also visite the deployed website [LipstickExpert](https://lipstickexpert.netlify.app/)


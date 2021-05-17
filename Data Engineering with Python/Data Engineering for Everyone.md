# Data Engineering for Everyone

## What is Data Engineering?

<!--buraya slayt notları gelecek-->
- **Data Workflow**
  1. Data Collection & Storage
  2. Data Preparation
  3. Exploration & Visualization
  4. Experimentation & Prediction
- Ingest data from different sources
- Optimize databases for analysis
- Remove corrupted data
- Develop, construct, test and maintain data architectures
- **5V**:
  - Volume (*how much*)
  - Variety (*what kind*)
  - Velocity (*how frequent*)
  - Veracity (*how accurate*)
  - Value (*how useful*)
- **Flow**
  1. Data collection and storage
  2. Data preparation
  3. Exploration and visualization
  4. Experimentation and prediction
- **Data Engineering Tasks**
  - Optimizing the customers databases for analysis.
  - Gathering music consumption data from desktop and mobile sources.
  - Ensuring corrupted, unreadable music tracks are removed and don't end up facing customers.
- **NOT Data Engineering Tasks**
  - Running an experiment to identify the optimal search bar positioning in the app.
  - Based on their listening behavior, predict which songs customers are likely to enjoy.
  - Building a visualization to understand listening patterns by city.
- **TRUE**
  - Data types refer to the variety of the data.
  - Value refers to how actionable the data is.
- **FALSE**
  - Volume has to with how trustworthy the data is.
  - Velocity refers to how big the data is.
  - Veracity refers to how frequently the data is generated.
- **DATA ENGINEER**
  - Use Java to buid a pipeline collecting album covers and storing them.
  - Provide listening sessions data so it can be analyzed with minimal preparation work.
  - Ensure that people who use the databases can't erase music videos by mistake.
- **DATA SCIENTIST**
  - Find out in which countries certain artists are popular to give them insights on where to tour.
  - Identify which customers are likely to end their Account subscriptions, so marketing can target them and encourage them to renew.
  - Use Python to run an analysis and understand whether users prefer having the search bar on the top left or the top right of the desktop App.
- **Automate**
  - Extracting
  - Transforming
  - Combining
  - Validating
  - Loading
- **Reduce**
  - Human Intervention
  - Errors
  - Time it takes data to flow
- **Data pipelines**
  - Move data from one system to another
  - May follow ETL (Extract, transform and Load)
  - Data may not be transformed
  - Data may be directly loaded in applications

## Storing Data

<!--buraya slayt-->
- **Structured**
  - Is easy to search and organize.
  - Is created and queried using SQL.
  - Corresponds to data in tabular format.
  - Consistent model, rows and columns.
  - Defined types.
  - Stored in relational databases.
- **Semi-Structured**
  - Is stored in *XML/JSON* format or in *NoSQL* databases.
  - Consistent model, less-rigid implementation: different obserations have different sizes.
  - Different types.
  - Can be grouped, but needs more work.
  - Follows a model while allowing more flexibility than structured data.
  - Is moderately easy to search and organize.
- **Unstructured**
  - Is difficult to search and organize.
  - Stores images, pictures, videos and text.
  - Is usually stored in data lakes.
  - Does not follow a model, can't be contained in rows and columns.
  - Most of the data is unstructured.
  - Can be extremely valuable.
- **DATA SCIENTIST**
  - Modifying the whole songs table to remove trailing spaces entered by mistake in front of the title.
  - Updating an artist's table after they edited their biography.
  - Creating a new table to store the songs customers listened ot the most of the pas tear.
- **DATA SCIENTIST**
  - Querying the top songs of the past year to identify which genre dominated.
  - Querying the lyrics table to find all the songs that have *data* in the title.
  - Querying the artist table to find all the bands that come from France.
- **Data Lake**
  - Stores all the raw data
  - Can be petabytes
  - Stores all data structures
  - Cost-effective
  - Difficult to analyze
  - Requires an up-to-date data catalog
  - Used by data scientists
  - Big data, real-time analytics
- **Data Warehouse**
  - Specific data for specific use
  - Relatively small
  - Stores mainly structured data
  - More costly to update
  - Optimized for data analysis
  - Also used by data analysts and business analysts
  - Ad-hoc, read-only queries
- **Data Catalog for Data Lakes**: It's information about data.

## Moving and Processing Data

- **Data Processing**: Converting *raw* data into *meaningful* information.
  - Remove unwanted data
  - Optimize memoryi process and network costs
  - Convert data from one type to another
  - Organize data
  - To fit into a schema/structure
  - Increase productivity
- **EXTRACT**
  - Pulling the top 20 songs user have benn listening to on a loop.
  - Collecting data from Google Analytics about our web-marketing promotion offering 3 months of access to the permium tier.
- **TRANSFORM**
  - Sorting a playlist's songs based on the date they were added.
  - Summarizing the yearly listening activity to tell users how many hours they have listened to music on App this year.
- **Scheduling** (*manual, time and sensor*)
  - Can apply to any task listed in data processing
  - Scheduling is the glue of your system
  - Holds each piece and organize how they work together
  - Runs tasks in a specific order and resolves all dependencies
- **LOAD**
  - Writing all the followers of a user in a table.
  - Saving the new order of a playlist that was sorted based on the date songs were added, so that it remains that way the next time the user connects.
- **MANUAL**
  - Running the song encoding pipeline, because enginerring changed the encoder and wants to make sure they still pass the validation check.
  - Running the pipeline processing sign ups because in the past 10 minutes, 100 new users complained to support that they can't connect.
- **TIME**
  - Generating the App weekly playlist from Chapter 1 every Monday at 00:00 AM.
  - Processing music videos uploaded by artists every hour.
  - Collecting data from Google Analytics every morning to check how the promotion campaign is going.
- **CONDITION**
  - Running validation checks if new videos are being collected.
  - Updating the number of followers in a playlist table after a user subcribed to it.
- **BATCH**
  - Loading new employees to App's employee table.
  - Reducing access to premium features when someone unsubscribes.
- **STREAM**
  - When a user listens to songs that are being recommended in real time, loading his upvotes and downvotes on each song.
  - Updating the couont of followers in a playlist when a user subcribes to it.
- **Batches**: Group records at intervals, Ofter cheaper.
- **Streams**: Send individual records right away.
- **Parallel Computing** Mainly necessary because of memory consumption, also providing for processing power. It splits tasks up into several smaller subtasks and distribute these subtasks over several computers.
  - [+] Extra processing power
  - [+] Reduced memory footprint
  - [-] Moving data incurs a cost
  - [-] Communication time
- **Multicloud**
  - [+] Reducing reliance on a single vendor
  - [+] Cost-efficiencies
  - [+] Local laws requiring certain data to be physically present within the country
  - [+]militating against disasters
  - [-] Cloud providers try to lock in consumers
  - [-] Incompatibility
  - [-] Security and governance

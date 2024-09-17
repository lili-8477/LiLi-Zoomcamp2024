# LiLi-Zoomcamp2024
## DE_EndToEnd_deployment
- module1 environment setup
  * containerize code with docker
    this will help us containerize the ingest_data.py code into a docker image based on the Dockfile
  ```bash
  docker build -t taxi_ingest:v001 .
  ```
   Run the image
  ```bash
  URL="https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz"

  docker run -it \
    --network=pg-network \
    taxi_ingest:v001 \
      --user=root \
      --password=root \
      --host=pg-database \
      --port=5432 \
      --db=ny_taxi \
      --table_name=yellow_taxi_trips \
      --url=${URL}
  ```
  * use docker-compose to combine multiple container.
  ```bash
  docker-compose up
  docker-compose down
  ```  



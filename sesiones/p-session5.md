# Partitions

# Create and Modify a Partitioned Table

  SHOW VARIABLES LIKE 'innodb_file_per_table';
  SET GLOBAL innodb_file_per_table=ON;
  USE world;
  CREATE TABLE City_part LIKE City;
  SHOW TABLE STATUS LIKE 'City_part'\G
  ALTER TABLE City_part PARTITION BY RANGE (ID) (
  PARTITION p0 VALUES LESS THAN (1000),
  PARTITION p1 VALUES LESS THAN (2000),
  PARTITION p2 VALUES LESS THAN (3000),
  PARTITION p3 VALUES LESS THAN MAXVALUE
  );
  SHOW TABLE STATUS LIKE 'City_part'\G
  INSERT INTO City_part SELECT * FROM City;
  
  cd /var/lib/mysql/world_innodb; ls -l
  
  EXPLAIN PARTITIONS SELECT * FROM City_parts\G;
  EXPLAIN PARTITIONS SELECT * FROM City_part WHERE ID < 2000\G
  ALTER TABLE City_part PARTITION BY KEY (ID) PARTITIONS 3;
  EXPLAIN PARTITIONS SELECT * FROM City_part\G
  
  cd /var/lib/mysql/world_innodb; ls -l
  
  SELECT TABLE_NAME,
  GROUP_CONCAT(PARTITION_NAME)
  FROM INFORMATION_SCHEMA.PARTITIONS
  WHERE TABLE_SCHEMA='world_innodb'
  AND TABLE_NAME='City_part';

# Remove Partitions from a Table

  ALTER TABLE City_part DROP PARTITION p0;
  ALTER TABLE City_part PARTITION BY RANGE (id) (
  PARTITION p0 VALUES LESS THAN (1000), 
  PARTITION p1 VALUES LESS THAN (2000), 
  PARTITION p2 VALUES LESS THAN (3000), 
  PARTITION p3 VALUES LESS THAN MAXVALUE );
  ALTER TABLE City_part DROP PARTITION p0;
  EXPLAIN PARTITIONS SELECT * FROM City_part\G
  
  cd /var/lib/mysql/world_innodb; ls -l
  
  ALTER TABLE City_part REMOVE PARTITIONING;
  SHOW TABLE STATUS LIKE 'City_part'\G
  EXPLAIN PARTITIONS SELECT * FROM City_part\G
  EXIT
  
  cd /var/lib/mysql/world_innodb; ls -l








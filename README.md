# rdb_exporter
This is a prometheus exporter for DBMS "Red Database".
# Exported metrics
<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr><td>RedDatabase_db_size</td><td>The amount of database bytes which are taken to store data.</td></tr>
  <tr><td>RedDatabase_diff_oldt_nt</td><td>The difference between Oldest transaction number and Next transaction number.</td></tr>
  <tr><td>RedDatabase_active_users</td><td>The amount of active users in a database. (Note: you need to have an administrator rights to extract this metric)</td></tr>
  <tr><td>RedDatabase_mon_reads</td><td>The amount of read pages of database.</td></tr>
  <tr><td>RedDatabase_mon_writes</td><td>The amount of recorded pages of database.</td></tr>
  <tr><td>RedDatabase_mon_fetches</td><td>The amount of loaded in memory pages of database.</td></tr>
  <tr><td>RedDatabase_mon_marks</td><td>The amount of marked in memory pages of database. These pages are "dirty" or are changed in memory but till have not written on disk</td></tr>
  <tr><td>RedDatabase_used_memory</td><td>The amount of used memory bytes.</td></tr>
</table>

# Exporter configuration file
You need to add a configuration json file beside "main.py" file and name it <strong>"exporter_conf"</strong> and fill it with a content.
<br>
The example of required content is:
```
{
  "port": 8000, 
  "login":  "SYSDBA", 
  "password":  "masterkey", 
  "databases": {
    "[db_nickname]": "localhost:[insert_path_to_database]",
    "[another_db_nickname]": "localhost:[insert_path_to_another_database]"
  }
  "utilities": "[insert_path_to_folder_with_utilities]"
}
```
<p><strong>Path to utilities folder must contain next following binary files:</strong></p>
<ul>
  <li>gstat</li>
  <li>isql</li>
</ul>

# Libraries
You need to install next following libraries to make the exporter work:
<ul>
  <li><strong>psutil</strong> (pip install psutil)</li>
</ul>

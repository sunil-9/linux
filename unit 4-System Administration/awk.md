<!-- `cat auth.log | grep "Failed password"`
`cat auth.log | grep "Failed password" | awk '{print $1}'`
`cat auth.log | grep "Failed password for invalid" | awk '{print $1 $2 $3 $13}'`
`cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}'`
`cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}' | sort | uniq -c | awk '{print $2, $3, $4, $5, $6, $1}'`
`cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}' | awk '{ip_count[$4]++} END {for (ip in ip_count) print $1, $2, $3, ip, $14, $15, ip_count[ip]}' | sort`
`cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}' | awk '{ip_count[$4]++} END {for (ip in ip_count) print $1, $2, $3, ip, $14, $15, ip_count[ip]}' | sort | tr ' ' ',' > authentication_failures.csv` -->


# Analyzing Authentication Failures in Linux Logs

Linux system administrators often need to monitor authentication failures in system logs to identify and address security threats. The `auth.log` file is one such log that contains valuable information about authentication attempts. In this blog, we will explore seven commands that can help you analyze authentication failure logs.

## Sample Input Data

We'll be working with a sample `auth.log` file containing various authentication events. Here's a snippet of the sample data:

```
Nov  1 08:19:20 ip-172-31-94-205 sshd[454487]: pam_unix(sshd:auth): check pass; user unknown
Nov  1 08:19:23 ip-172-31-94-205 sshd[454487]: Failed password for invalid user centos from 118.41.204.72 port 49772 ssh2
Nov  1 08:20:58 ip-172-31-94-205 sshd[454583]: Invalid user supervisor from 122.176.30.69 port 40798
Nov  1 08:39:42 ip-172-31-94-205 sshd[459681]: Failed password for root from 106.51.71.157 port 50397 ssh2
...
```

## Command 1: Filtering Authentication Failure Events

The first command filters out lines containing "Failed password" from the `auth.log`:

```bash
cat auth.log | grep "Failed password"
```

**Output (Sample):**
```
Nov  1 08:19:23 ip-172-31-94-205 sshd[454487]: Failed password for invalid user centos from 118.41.204.72 port 49772 ssh2
Nov  1 08:39:42 ip-172-31-94-205 sshd[459681]: Failed password for root from 106.51.71.157 port 50397 ssh2
...
```

This command extracts lines where authentication failures occurred.

## Command 2: Extracting Timestamps

The second command extracts the timestamps (date and time) from the authentication failure events:

```bash
cat auth.log | grep "Failed password" | awk '{print $1}'
```

**Output (Sample):**
```
Nov
Nov
...
```

This command helps in understanding when the authentication failures took place.

## Command 3: Extracting Relevant Information

The third command extracts key information, including the date, time, source IP, and username of authentication failures for invalid users:

```bash
cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13}'
```

**Output (Sample):**
```
Nov  1 08:19:23 118.41.204.72
Nov  1 08:20:58 122.176.30.69
...
```

This command provides a more focused view of authentication failure events.

## Command 4: Detailed Information

The fourth command extracts additional information, such as the date, time, source IP, username, and port number:

```bash
cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}'
```

**Output (Sample):**
```
Nov  1 08:19:23 centos 118.41.204.72 port 49772
Nov  1 08:20:58 supervisor 122.176.30.69 port 40798
...
```

This command provides more context about authentication failures.

## Command 5: Sorting Events

The fifth command counts and sorts unique authentication failure events:

```bash
cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}' | sort 
```

**Output (Sample):**
```
Nov 1 08:19:23 centos 118.41.204.72 port 49772
Nov 1 08:20:58 supervisor 122.176.30.69 port 40798
...
```

This command helps identify the frequency of each unique authentication failure event.

## Command 6: Aggregating and Sorting by IP

The sixth command aggregates events by source IP, counts them, and sorts the results:

```bash
cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}' | awk '{ip_count[$4]++} END {for (ip in ip_count) print $1, $2, $3, ip, $4, $5, ip_count[ip]}' | sort
```

**Output (Sample):**
```
Nov 1 08:20:58 122.176.30.69 port 40798 1
Nov 1 08:19:23 118.41.204.72 port 49772 1
...
```

This command helps you identify which source IPs are involved in multiple authentication failures.

## Command 7: Geolocating IP Addresses

The seventh command adds geolocation information to source IP addresses using a tool like `geoiplookup`:
- you may need to install the `geoiplookup` tool using `sudo apt install geoip-bin` before running this command.

```bash
cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}' | awk '{ip_count[$4]++} END {for (ip in ip_count) print $1, $2, $3, ip, $4, $5, ip_count[ip]}' | sort | while read line; do ip=$(echo $line | awk '{print $4}'); location=$(geoiplookup $ip); echo "$line $location"; done
```

**Output (Sample):**
```
Nov 1 08:20:58 122.176.30.69 port 40798 1 GeoIP Country Edition: IN, India
Nov 1 08:19:23 118.41.204.72 port 49772 1 GeoIP Country Edition: KR, South Korea
...
```

This command enhances the analysis with geolocation data for source IPs.

## Command 8: Exporting data

You can separate the output with commas (,) and save the output to your local machine as a CSV file:

```bash
cat auth.log | grep "Failed password for invalid" | awk '{print $1, $2, $3, $13, $14, $15}' | awk '{ip_count[$4]++} END {for (ip in ip_count) print $1, $2, $3, ip, $4, $5, ip_count[ip]}' | sort | while read line; do ip=$(echo $line | awk '{print $4}'); location=$(geoiplookup $ip); echo "$line $location"; done | tr ' ' ',' > authentication_failures.csv
```

**Output (Sample):**
```

```

This command exports the output to a CSV file and your console output will be empty.



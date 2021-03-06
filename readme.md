# Cron Job Scheduling System

Used thrift as RPC framework.

# IDL
```
exception JobServiceException{
    1: i32 code,
    2: string msg,
    3: string time,
    4: string detail
}

service JobRPCService{

    void start_scheduler() throws (1: JobServiceException ex)

    void stop_scheduler() throws (1: JobServiceException ex)

    void pause_scheduler() throws (1: JobServiceException ex)

    void resume_scheduler() throws (1: JobServiceException ex)

    void start_job(1: string job_id) throws (1: JobServiceException ex)

    void stop_job(1: string job_id) throws (1: JobServiceException ex)

    void pause_job(1: string job_id) throws (1: JobServiceException ex)

    void modify_job(1: string job_id, 2: string config) throws (1: JobServiceException ex)

    string submit_job(1: string file_bytes, 2: string config) throws (1: JobServiceException ex)

    # 0 停止，1 运行，2暂停
    i32 status() throws (1: JobServiceException ex)
}

```
# How to run

 - Create the table in `sql/create_table.sql`
 - `./run.sh prod` (dev, test, prod)

# Log

## v1.0.0

- Basic cron job scheduling.
- LeetCode auto sign in script.
- 1point3acres auto sign in script.
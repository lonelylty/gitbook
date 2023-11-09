由于锁 Monitor  是线程独占式访问的，所以其对性能的影响还是蛮大的，那有没有一种方式可是实现：允许多个线程同时读数据、只允许一个线程写数据呢

读写锁 ReaderWriterLockSlim 、就是 支持单个写线程和多个读线程的锁

```c#
using System;
using System.Collections.Generic;
using System.Threading;

public class LockExample
{
    private static ConcurrentDictionary<string, ReaderWriterLockSlim> tableLocks = new ConcurrentDictionary<string, ReaderWriterLockSlim>();
    private static ConcurrentDictionary<string, ReaderWriterLockSlim> rowLocks = new ConcurrentDictionary<string, ReaderWriterLockSlim>();

    public void LockTable(string tableName)
    {
        ReaderWriterLockSlim tableLock;

        lock (tableLocks)
        {
            if (!tableLocks.TryGetValue(tableName, out tableLock))
            {
                tableLock = new ReaderWriterLockSlim();
                tableLocks.Add(tableName, tableLock);
            }
        }

        tableLock.EnterWriteLock();
    }

    public void UnlockTable(string tableName)
    {
        ReaderWriterLockSlim tableLock;

        lock (tableLocks)
        {
            if (tableLocks.TryGetValue(tableName, out tableLock))
            {
                tableLock.ExitWriteLock();
            }
            else
            {
                Console.WriteLine("Table is not locked.");
            }
        }
    }

    public void LockRow(string rowId)
    {
        ReaderWriterLockSlim rowLock;

        lock (rowLocks)
        {
            if (!rowLocks.TryGetValue(rowId, out rowLock))
            {
                rowLock = new ReaderWriterLockSlim();
                rowLocks.Add(rowId, rowLock);
            }
        }

        rowLock.EnterWriteLock();
    }

    public void UnlockRow(string rowId)
    {
        ReaderWriterLockSlim rowLock;

        lock (rowLocks)
        {
            if (rowLocks.TryGetValue(rowId, out rowLock))
            {
                rowLock.ExitWriteLock();
            }
            else
            {
                Console.WriteLine("Row is not locked.");
            }
        }
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        LockExample lockExample = new LockExample();

        // 锁定表
        lockExample.LockTable("Products");

        // 锁定行
        lockExample.LockRow("1");

        // 解锁行
        lockExample.UnlockRow("1");

        // 解锁表
        lockExample.UnlockTable("Products");
    }
}

```
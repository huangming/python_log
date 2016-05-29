# python_log
a simple encapsulation of logging module to provide a more
convenient interface to write log.The log will both print to stdout and
write to log file. It provides a more flexible way to set the log actions,
and also very simple. See examples showed below:
 
Example 1: Use default settings
 
    import log
    log = log.Log(cmdlevel='info')
    log.debug('hello, world')
    log.info('hello, world')
    log.error('hello, world')
    log.critical('hello, world')
 
Result:
Print all log messages to file, and only print log whose level is greater
than ERROR to stdout. The log file is located in 'xxx.log' if the module 
name is xxx.py. The default log file handler is size-rotated, if the log 
file's size is greater than 20M, then it will be rotated.
 
Example 2: Use set_logger to change settings
 
    # Change limit size in bytes of default rotating action
    log.set_logger(limit = 10240) # 10M
 
    # Use time-rotated file handler, each day has a different log file, see
    # logging.handlers.TimedRotatingFileHandler for more help about 'when'
    log.set_logger(when = 'D', limit = 1)
 
    # Use normal file handler (not rotated)
    log.set_logger(backup_count = 0)
 
    # File log level set to INFO, and stdout log level set to DEBUG
    log.set_logger(cmdlevel = 'DEBUG', filelevel = 'INFO')
 
    # Change default log file name and log mode
    log.set_logger(filename = 'yyy.log', mode = 'w')
 
    # Change default log formatter
    log.set_logger(cmdfmt = '[%(levelname)s] %(message)s')




# study-exercise
# Write a program to read through the mbox-short.txt and figure out the distribution by hour of the day for each of the messages.  

fname = raw_input('Enter the file name: ')
try:
    fhand = open(fname)
except:
    print 'File cannot be opened:', fname
    exit()

counts = dict()

for line in fhand:
    if line.startswith('From '):
        words = line.split()
        time = words[5]
        day = time.split(':')
        hour = day[0]
        counts[hour] = counts.get(hour,0) + 1

lst = list()
for key in counts:
  value = counts[key]
  lst.append( (key, value) ) 

lst.sort()

for key, value in lst:
  print key, value

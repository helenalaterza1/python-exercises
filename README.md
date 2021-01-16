""
python-exercises
A series of exercises from "Python for everybody - a course from the University of Michigan

10.2 Write a program to read through the mbox-short.txt and figure out the distribution by hour of the day for each of the messages. You can pull the hour out from the 'From ' line by finding the time and then splitting the string a second time using a colon.
From stephen.marquard@uct.ac.za Sat Jan  5 09:14:16 2008
Once you have accumulated the counts for each hour, print out the counts, sorted by hour as shown below.
""

name = input("Enter file:")
if len(name) < 1 : name = "mbox-short.txt"
handle = open(name)

#Finding usefull lines - adding the full hours to a list

lst = list()

for line in handle:
    if line.startswith('From:'): continue
    if line.startswith('From'):
        words = line.split()
        lst.append(words[5])

#Adding only the hours (not minutes and seconds) to a list

hrs = list()
        
for hours in lst:
    hrs.append(hours[0:2])

#Creating a dictionary to count occurences of each hour
    
counts = dict()

for fhours in hrs:
    counts[fhours] = counts.get(fhours,0) + 1
        
#Creating list of tuples to sort dictionary

sorted_hours = list()

for k, v in counts.items():
    sorted_hours.append((k,v))
    
sorted_hours = sorted(sorted_hours)
    
for k,v in sorted_hours:
    print(k,v)

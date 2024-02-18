# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 18-02-24 [Problem Link](https://leetcode.com/problems/meeting-rooms-iii/description/?envType=daily-question&envId=2024-02-18)
## 2402. Meeting Rooms III

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

- To efficiently track the availability of rooms, I can use a priority queue to manage occupied rooms based on their end times.
- Additionally, I can use another priority queue to keep track of available room IDs.
- Sorting the meetings based on their start times will ensure that I process the meetings in chronological order.

# Approach
<!-- Describe your approach to solving the problem. -->

- I initialized an array to store the count of meetings booked for each room (`meetingCount`).
- Sorted the meetings based on their start times.
- Initialized a priority queue (`occupiedRooms`) to store occupied rooms based on end times.
- Initialized another priority queue (`availableRoomIds`) to store available room IDs.
- Populated the `availableRoomIds` priority queue with the initial room IDs.
- Processed each meeting in chronological order:
   - Moved meetings ending before the current meeting to available rooms from `occupiedRooms`.
   - If no available rooms, scheduled the meeting in the room with the earliest end time from `occupiedRooms`.
   - Otherwise, scheduled the meeting in an available room from `availableRoomIds`.
- Updated the `meetingCount` array with the count of meetings booked for each room.
- Found the room with the maximum booked meetings and return its index.

My approach ensured efficient tracking of occupied and available rooms, allowing for the determination of the most frequently booked room.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O(m*logm)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$m$ :  number of meetings
- Space complexity : $O(m)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
import java.util.Arrays;
import java.util.PriorityQueue;
import java.util.Queue;

// Defining a class to represent a meeting with endTime and roomId
class Meeting {
    public long endTime;
    public int roomId;

    public Meeting(long endTime, int roomId) {
        this.endTime = endTime;
        this.roomId = roomId;
    }
}

// Class for meeting scheduling and finding the most booked room
class Solution {

    static Queue<Meeting> occupiedRooms;
    static Queue<Integer> availableRoomIds;
    
    // Method to find the most booked room
    public int mostBooked(int numberOfRooms, int[][] meetings) {
    
        // Array to store the count of meetings booked for each room
        int[] meetingCount = new int[numberOfRooms];

        // Sorting meetings based on start time
        Arrays.sort(meetings, (a, b) -> a[0] - b[0]);

        // Priority queue to store occupied rooms based on end time
        occupiedRooms = new PriorityQueue<>((a, b) ->
                a.endTime == b.endTime ? Integer.compare(a.roomId, b.roomId) : Long.compare(a.endTime, b.endTime));

        // Priority queue to store available room IDs
        availableRoomIds = new PriorityQueue<>();

        // Initializing available room IDs
        for (int i = 0; i < numberOfRooms; ++i) {
            availableRoomIds.offer(i);
        }

        // Processing each meeting
        for (int[] meeting : meetings) {
            final int start = meeting[0];
            final int end = meeting[1];

            // Moving meetings ending before the current meeting to available rooms
            while (!occupiedRooms.isEmpty() && occupiedRooms.peek().endTime <= start) {
                availableRoomIds.offer(occupiedRooms.poll().roomId);
            }

            // If no available room, scheduling the meeting in the room with the earliest end time
            if (availableRoomIds.isEmpty()) {
                Meeting prevMeeting = occupiedRooms.poll();
                ++meetingCount[prevMeeting.roomId];
                occupiedRooms.offer(new Meeting(prevMeeting.endTime + (end - start), prevMeeting.roomId));
            } 
            else {
                // Scheduling the meeting in an available room
                final int roomId = availableRoomIds.poll();
                ++meetingCount[roomId];
                occupiedRooms.offer(new Meeting(end, roomId));
            }
        }

        // Finding the room with the maximum booked meetings
        int maxIndex = 0;
        for (int i = 0; i < numberOfRooms; ++i) {
            if (meetingCount[i] > meetingCount[maxIndex]) {
                maxIndex = i;
            }
        }

        return maxIndex;
    }
}

```
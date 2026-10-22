# [Shop Scheduling] Flexible Shop Scheduling Based on SPT Rules (Python Code Implementation)

Flexible workshop static and dynamic scheduling based on SPT dispatching rules (Python code implementation)
Main function code:
NoPythonDo not download, do not answer.from algorithms import prepareJobs, algorithmSPT\nfrom rescheduleAlgorithms import *\nfrom ganttCreator import createGanttChart\nfrom parseData import parseData\nimport copy\nfrom parseNewData import parseNewData\n\n\ndef main():\n    machinesList, itinerariesList = parseData(input("Please enter the data save path.: "))\n    jobsList = prepareJobs(machinesList, itinerariesList)\n    resultSPT = algorithmSPT(copy.deepcopy(jobsList), machinesList)\n    createGanttChart(resultSPT, machinesList, itinerariesList)\n    loop = True\n    while loop:\n        yourChoice = input("Is there a need for re-scheduling?? [y/n]:")\n        if yourChoice == "y":\n            rescheduleTime = float(input("Please enter the reschedule time (0~CmaxBetween): "))\n            print("Please select re-scheduling method: ")\n            print(30 * "-", "MENU", 30 * "-")\n            print("1. Insert emergency order")\n            print("2. Change the priority of unfinished workpieces")\n            print("3. Machine failure")\n            print("4. Exit")\n            print(66 * "-")\n            rescheduleChoice = input("Enter your choice [1-4]: ")\n            if rescheduleChoice == "1":\n                savePath = input("Please enter the emergency order save path[File path]:")\n                insertItineraryList = parseNewData(savePath)\n                insertJobList = prepareJobs(machinesList, insertItineraryList)\n                resultInsertReschedule = rescheduleInsertJobsSPT(resultSPT, rescheduleTime, insertJobList, machinesList)\n                insertItineraryList.extend(itinerariesList)\n                createGanttChart(resultInsertReschedule, machinesList, itinerariesList, rescheduleTime)\n            elif rescheduleChoice == "2":\n                priorItinerary = int(input("Please enter the priority of the workpiece number.:"))\n                resultPriorReschedule = recheduleChangePriority(resultSPT, rescheduleTime, priorItinerary, machinesList)\n                createGanttChart(resultPriorReschedule, machinesList, itinerariesList, rescheduleTime)\n            elif rescheduleChoice == "3":\n                faultyMachine = input("Please enter the machine number that has failed[As such.: M3]: ")\n                resultFaultyReschedule = recheduleMachineFault(resultSPT, rescheduleTime, faultyMachine, machinesList)\n                createGanttChart(resultFaultyReschedule, machinesList, itinerariesList, rescheduleTime)\n            elif rescheduleChoice == "4":\n                return 0\n        elif yourChoice == "n":\n            return 0\n\nif __name__ == '__main__':\n    main()\n\n  

## Images

![(Shop Scheduling)Flexible Shop Scheduling Based on SPT Rule (Python Code Implementation)](cover.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->

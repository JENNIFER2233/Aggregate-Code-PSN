# Aggregate-Code-PSN
import os

#Initialize aggegate variable
aggregate =0

#Path to the directory containing the prediction
prediction_base_dir = "/scratch/jmorones/dyn_psn"

#Iterate through PSN folders (0 to 72)
for psn_number in range(73):
  psn_folder_path = prediction_base_dir + "/dyn_psn" + str(psn_number)

#Iterate through pediction files (0 to 5) with each PSN folder
  for prediction_number in range(6):
    prediction_file_path = psn_folder_path + "/output/Classification-result/Prediction" + str(prediction_number) + ".txt"
        

#Process the file and extract necessary data
with open(prediction_file_path, 'r') as file:
  protein_label = file.readline().strip()
  protein_actual = float(file.readline().strip())  
  protein_prediction = float(file.readline().strip()) 


#Calculate the aggregate for each prediction file 
prediction_aggregate = protein_actual + protein_prediction

#Update the aggregate value 
aggregate += prediction_aggregate

#Print the final aggregate value
print("The aggegate is:",aggregate)

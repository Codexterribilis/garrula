"Running a program":


To train the model: 

1. Set mode ="train" in configuration file setModelParams.rc. 2. Delete the content of checkpoint folder so that it can do a fresh start. If not deleted, then the program will pickup the latest checkpoint file and start training from it. 3. run garrula.py on command line. (python garrula.py)

To test the model: 

1. Set mode="test" in configuration file setModelParams.rc. 
2. copy the checkpoint_after5day_training/ to checkpoints/ (To get good results, otherwise can be tested from any generated CHECKPOINTS.). 
3. run garrula.py using command line. (python garrula.py)

NOTE: This model is to be trained only once from the scratch till it reaches a lower value learning rate. We have previously trained it for over 5 days to reach a learning rate of 0.0001. A checkpoint of that execution is provided in folder checkpoint_after5day_training/. The program is created in such a way that it picks up the learning rate from the LATEST CREATED CHECKPOINT. We suggest to take a backup the checkpoint in checkpoint_after5day_training/ to match the results from the one which you have trained on for less time with a higher Learning rate(for Testing only). It will help you understand how Lower value of Learning rate helps to increase the performace of the Model.


Procedure for Testing model performance as mentioned above: 

1. Run the program in "Train" mode. 
2. Either use the checkpoints in the checkpoints/ to test the results or 
3. Delete the checkpoints and their metadata from checkpoints/ and copy the already trained checkpoint_after5day_training/ to checkpoints/ . 
4. Later can compare the results for your understanding.

Note: We can also visualize a TensorFlow graph and the computations happening through tensorboard API. It helps in coding the TensorFlow graph incrementaly. Steps to run the graph visualization:
1.go into tensorboard/logs/
2.and run tensorboard --logdir=.
3.open the link which got generated from step 2
4.go to GRAPHS tab.(we have attached the output in sample_results&output/) 

--model parameters---(for training which has been set to default )
learning_rate LEARNING_RATE                           			        |Learning rate.                         	
learning_rate_decay_factor LEARNING_RATE_DECAY_FACTOR 		        	|Learning rate decays    	    
max_gradient_norm MAX_GRADIENT_NORM                   	        		|Clip gradients          	    
STEPS_PER_CHECKPOINT STEPS_PER_CHECKPOINT      		 		            |training steps per checkpoint.

--Neural Network Architecture--

batch_size BATCH_SIZE           		                                |Batch size during training.     
size SIZE                                          		                |Size of each model layer.              
num_layers NUM_LAYERS                                                   |Number of layers in the model.         
vocab_size VOCAB_SIZE                                                   |Vocabulary size.                       
model_type MODEL_TYPE        				                            |encoder_decoder RNN with attention mechanism.
buckets BUCKETS                                      		           	|Implement the model with buckets            max_sentence_length  MAX_SENTENCE_LENGTH  	  		               	 |Maximum sentence length for model WITHOUT buckets.
************************************************************************************************************************

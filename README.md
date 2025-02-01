# ✅ Boundary-Unlearning

**Boundary Unlearning**

Rapid Forgetting of Deep Networks via Shifting the Decision Boundary 

*CVPR 2023*
*Min Chen, Weizhuo Gao, Gaoyang Liu, Kai Peng, Chen Wang Hubei Key Laboratoryof Smart Internet Technology, School of EIC, Huazhong University of Science and Technology, Wuhan 430074, China*

## ▶️ Boundary shrink
- Breaking the decision boundary of the forgetting class by splitting the forgetting feature space into other classes.

## ▶️ Boundary expanding
- Dispersing the activation of the forgetting class by remapping an extra shadow class assigned to the forgetting data and then pruning it.

## ▶️ Contribution
- Neither costs too much computational resource nor intervenes the original training pipeline.
- Rapidly achieve the utility and privacy guarantees with only a few epochs of boundary adjusting.

## ▶️ Method – Boundary Shrink
- Fine-tune the model with randomly assigned labels to forgetting data? => boundary of remaining data also will be shifted. (side effect!)
- So, Fine-tune with the nearest but incorrect class in the feature space => the boundary of the surrounding class absorbs the boundary of the forgetting data!

![image](https://github.com/user-attachments/assets/d95e786f-3af7-4976-b003-abb984abb4cd)

- Like Adversarial attacks, add noise to the forgetting sample using the gradient sign of the loss function of the original model. 
- Obtain the nearest but incorrect label of the adversarial sample.
- Reassign the label on the forgetting sample and fine-tune it.

## ▶️ Performance evaluation – Experimental setting
- **Dataset:** CIFAR-10(All-CNN)
- **Original:** The initially trained model, which maintains high accuracy even with the Forget Set (Data to be forgotten).
- **Retrain:** A model retrained after completely removing the Forget Set, resulting in 0% accuracy for the Forget Set. (Goal)
- **Random Labels:** A technique where random labels are assigned to the Forget Set, confusing the model and causing a significant drop in overall performance.
- **Boundary Shrink (50%):** A model where the decision boundary related to the Forget Set is adjusted by 50%, reducing its impact on the model.
- **Boundary Shrink (100%):** A model where the decision boundary related to the Forget Set is fully adjusted, lowering its accuracy while maintaining the performance of the Retain Set.



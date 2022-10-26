import numpy as np
import pandas as pd

df = pd.DataFrame(np.random.randint(0, 2, size=(7, 7)), )
# df = pd.DataFrame([[0, 1, 1, 0, 0, 0, 0],
#                    [0, 0, 0, 0, 0, 0, 0],
#                    [1, 0, 0, 1, 1, 0, 0],
#                    [1, 0, 0, 1, 0, 0, 1],
#                    [0, 1, 1, 0, 1, 1, 1],
#                    [1, 1, 1, 1, 1, 0, 1],
#                    [0, 0, 1, 1, 0, 0, 1]])
result_visualization = ""
counter = 1
for row_n in range(7):
    for clmn_n in range(7):
        current_state = (df.iloc[[row_n]][clmn_n].values[0])
        temp_dict = {0: 0, 1: 0}

        try:
            temp_dict[df.iloc[[row_n - 1]][clmn_n].values[0]] += 1  # upper
            temp_dict[df.iloc[[row_n - 1]][clmn_n + 1].values[0]] += 1  # up_right
            temp_dict[df.iloc[[row_n]][clmn_n + 1].values[0]] += 1  # right
            temp_dict[df.iloc[[row_n + 1]][clmn_n + 1].values[0]] += 1  # down_right
            temp_dict[df.iloc[[row_n + 1]][clmn_n].values[0]] += 1  # down
            temp_dict[df.iloc[[row_n + 1]][clmn_n - 1].values[0]] += 1  # down_left
            temp_dict[df.iloc[[row_n]][clmn_n - 1].values[0]] += 1  # left
            temp_dict[df.iloc[[row_n - 1]][clmn_n - 1].values[0]] += 1  # up_left

        except IndexError:
            pass
        except KeyError:
            pass
        else:
            if current_state == 1:  # alive
                if 1 < temp_dict[1] < 4:  # 2 or 3 alive neighbours
                    pass
                elif temp_dict[1] < 2:  # 0 or 1 alive neighbours
                    df[row_n][clmn_n] = 0
                elif temp_dict[1] >= 4:  # 4 or more alive neighbours
                    df[row_n][clmn_n] = 0
            elif current_state == 0:  # death cell
                if temp_dict[1] == 3:  # 3 alive neighbours
                    df[row_n][clmn_n] = 1

        result_visualization += "\n" * 3 + f"After {counter} iteration" + "\n" * 2 + df.to_string()
        counter += 1

print(result_visualization)

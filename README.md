# Bai4_Buoi4_Nhom9_CNTT1809.ipynb
Bai4_Buoi4_Nhom9_CNTT1809.ipynb
def sinh_so_tam_phan(n):
    """
    Sinh tất cả các số tam phân (chỉ gồm 0,1,2) có độ dài n.
    """
    if n <= 0:
        print("Độ dài phải là số dương.")
        return

    print(f"Các số tam phân có độ dài {n}:")
    so_luong_so = 3**n

    for i in range(so_luong_so):
        # Chuyển số i sang hệ 3
        dang_tam_phan = ""
        x = i
        for _ in range(n):
            dang_tam_phan = str(x % 3) + dang_tam_phan
            x //= 3
        print(dang_tam_phan)

# Ví dụ: Sinh số tam phân độ dài 2
sinh_so_tam_phan(2)

print("\n--- Sinh số tam phân độ dài 3 ---")
sinh_so_tam_phan(3)



#bài  4.4.2
import itertools

def liet_ke_hoan_vi(danh_sach_phan_tu):
    """
    Liệt kê tất cả các hoán vị của một danh sách phần tử bằng thuật toán quay lui.
    """
    ket_qua = []  
    n = len(danh_sach_phan_tu)

    def backtrack(current_permutation, remaining_elements):
        if not remaining_elements:
            ket_qua.append("".join(map(str, current_permutation)))
            return

        for i in range(len(remaining_elements)):
            chon_phan_tu = remaining_elements[i]
            current_permutation.append(chon_phan_tu)
            new_remaining = remaining_elements[:i] + remaining_elements[i+1:]
            backtrack(current_permutation, new_remaining)
            current_permutation.pop()

    backtrack([], list(danh_sach_phan_tu))
    return ket_qua


# --- Liệt kê hoán vị của [1, 2, 3, 4] bằng quay lui ---
phan_tu_3 = [1, 2, 3, 4]
hoan_vi_3 = liet_ke_hoan_vi(phan_tu_3)

print(f"Các hoán vị của {phan_tu_3}:")
print(hoan_vi_3)
print(f"Tổng số hoán vị: {len(hoan_vi_3)}")  # -> 24


# --- So sánh với itertools.permutations ---
hoan_vi_itertools = list(itertools.permutations(phan_tu_3))
print("\nCác hoán vị với itertools:")
print(hoan_vi_itertools)
print(f"Tổng số hoán vị (itertools): {len(hoan_vi_itertools)}")  # -> 24

<script setup lang="ts">
import { ref, h, resolveComponent } from "vue";
import type { DropdownMenuItem, TableColumn } from "@nuxt/ui";
import type { Row } from "@tanstack/table-core";

const UBadge = resolveComponent("UBadge");
const UButton = resolveComponent("UButton");
const UDropdownMenu = resolveComponent("UDropdownMenu");
const toast = useToast();

type Record = {
  branchCode: string;
  branchName: string;
  executionDate: string;
  executor: string;
  canEdit: boolean;
  canLock: boolean;
};

const data = ref<Record[]>([
  {
    branchCode: "11",
    branchName: "مكتب الدراسات الاجتماعية",
    executionDate: "2024-11-11",
    executor: "علي الزهراني",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "10",
    branchName: "مكتب الدراسات الاجتماعية",
    executionDate: "2024-11-11",
    executor: "علي الزهراني",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "09",
    branchName: "مكتب الدراسات الاجتماعية",
    executionDate: "2024-11-11",
    executor: "علي الزهراني",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "08",
    branchName: "مكتب الدراسات الاجتماعية",
    executionDate: "2024-11-11",
    executor: "علي الزهراني",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "07",
    branchName: "مكتب الدراسات الاجتماعية",
    executionDate: "2024-11-11",
    executor: "علي الزهراني",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "06",
    branchName: "مكتب الدراسات الاجتماعية",
    executionDate: "2024-11-11",
    executor: "علي الزهراني",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "05",
    branchName: "مكتب الدراسات الاجتماعية",
    executionDate: "2024-11-11",
    executor: "علي الزهراني",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "04",
    branchName: "مكتب الجواد العربي",
    executionDate: "2024-10-11",
    executor: "سعيد القحطاني",
    canEdit: false,
    canLock: true,
  },
  {
    branchCode: "03",
    branchName: "اللجنة الاستشارية العليا للعمل على استكمال تطب...",
    executionDate: "2024-09-10",
    executor: "فهد العتيبي",
    canEdit: true,
    canLock: false,
  },
  {
    branchCode: "02",
    branchName: "مكتب تكريم الشهداء وأسرهم",
    executionDate: "2024-08-09",
    executor: "أحمد الشمري",
    canEdit: true,
    canLock: true,
  },
  {
    branchCode: "01",
    branchName: "شؤون الديوان الأميري",
    executionDate: "2024-07-23",
    executor: "منفذ من النظام",
    canEdit: false,
    canLock: false,
  },
  {
    branchCode: "00",
    branchName: "الديوان الأميري",
    executionDate: "2024-06-15",
    executor: "منفذ من النظام",
    canEdit: true,
    canLock: true,
  },
]);

const columns: TableColumn<Record>[] = [
  {
    id: "actions",
    cell: ({ row }) => {
      return h(
        "div",
        h(
          UDropdownMenu,
          {
            content: {
              align: "end",
            },
            items: getRowItems(row),
          },
          () =>
            h(UButton, {
              icon: "charm:menu-kebab",
              color: "neutral",
              variant: "ghost",
            })
        )
      );
    },
  },
  {
    id: "edit",
  },
  {
    id: "lock",
  },
  {
    accessorKey: "executor",
    header: ({ column }) => {
      const isSorted = column.getIsSorted();
      return h(UButton, {
        label: "منفذ عملية الإضافة",
        icon: isSorted
          ? isSorted === "asc"
            ? "i-lucide-arrow-up-narrow-wide"
            : "i-lucide-arrow-down-wide-narrow"
          : "uil:sort",
        variant: "ghost",

        color: "black",
        onClick: () => column.toggleSorting(column.getIsSorted() === "asc"),
      });
    },
    cell: ({ row }) => row.getValue("executor"),
  },
  {
    accessorKey: "executionDate",
    header: ({ column }) => {
      const isSorted = column.getIsSorted();
      return h(UButton, {
        label: "تاريخ تنفيذ الإضافة",
        icon: isSorted
          ? isSorted === "asc"
            ? "i-lucide-arrow-up-narrow-wide"
            : "i-lucide-arrow-down-wide-narrow"
          : "uil:sort",
        variant: "ghost",

        color: "black",
        onClick: () => column.toggleSorting(column.getIsSorted() === "asc"),
      });
    },
    cell: ({ row }) => row.getValue("executionDate"),
  },

  {
    accessorKey: "branchName",
    header: ({ column }) => {
      const isSorted = column.getIsSorted();
      return h(UButton, {
        label: "اسم الجهة الفرعية",
        icon: isSorted
          ? isSorted === "asc"
            ? "i-lucide-arrow-up-narrow-wide"
            : "i-lucide-arrow-down-wide-narrow"
          : "uil:sort",
        variant: "ghost",

        color: "black",
        onClick: () => column.toggleSorting(column.getIsSorted() === "asc"),
      });
    },
    cell: ({ row }) => row.getValue("branchName"),
  },
  {
    accessorKey: "branchCode",
    header: ({ column }) => {
      const isSorted = column.getIsSorted();
      return h(UButton, {
        label: "رمز الجهة الفرعية",
        icon: isSorted
          ? isSorted === "asc"
            ? "i-lucide-arrow-up-narrow-wide"
            : "i-lucide-arrow-down-wide-narrow"
          : "uil:sort",
        variant: "ghost",

        color: "black",
        onClick: () => column.toggleSorting(column.getIsSorted() === "asc"),
      });
    },
    cell: ({ row }) => row.getValue("branchCode"),
  },
];

const sorting = ref();

function getRowItems(row: Row<Record>): DropdownMenuItem[][] {
  return [
    [
      {
        label: "سجل العمليات",
        icon: "solar:clipboard-list-outline",
      },
      {
        label: "فتح ",
        icon: "fluent:lock-open-20-regular",
      },
      {
        label: "تعديل",
        icon: "solar:pen-new-square-outline",
      },
      {
        label: "حذف",
        icon: "fluent:delete-20-regular",
        // color: "error",
      },
    ],
  ];
}
function showToast() {
  toast.add({ title: "Toast" });
}
const page = ref(1);
const pageCount = 5;

const rows = computed(() => {
  return data.value.slice((page.value - 1) * pageCount, page.value * pageCount);
});
</script>

<template>
  <UTable
    :loading-state="{
      icon: 'i-heroicons-arrow-path-20-solid',
      label: 'Loading...',
    }"
    :empty-state="{
      icon: 'i-heroicons-circle-stack-20-solid',
      label: 'No items.',
    }"
    v-model:sorting="sorting"
    :data="rows"
    :columns="columns"
    class="flex-1"
    :ui="{ td: 'p-0 ', th: 'p-1' }"
  >
    <template #edit-cell="{ row }">
      <Icon
        size="20"
        name="solar:pen-new-square-outline"
        class="hover:text-gray-800 cursor-pointer"
        color="neutral"
        @click="showToast"
      />
    </template>
    <template #lock-cell="{ row }">
      <UBadge :variant="row.original.canLock ? 'success' : 'neutral'">
        <Icon
          size="20"
          :name="
            row.original.canLock
              ? 'fluent:lock-closed-20-regular'
              : 'fluent:lock-open-20-regular'
          "
          class="hover:text-gray-800 cursor-pointer"
          color="neutral"
        />
      </UBadge>
    </template>
  </UTable>
  <div
    class="flex justify-end px-3 py-3.5 border-t border-gray-200 dark:border-gray-700"
  >
    <UPagination
      v-model:page="page"
      :page-count="pageCount"
      :total="data.length"
      :items-per-page="5"
    />
  </div>
</template>

<script setup lang="ts">
</script>

<template>
  <Story
    title="App/Sidebar/AppSidebar"
  >
    <Variant title="Default">
      <div class="grid grid-cols-sidebar">
        <AppSidebar has-hidden>
          <AppSidebarCategory>
            <template #title>
              Category 1
            </template>
            <template #content>
              <AppSidebarItem to="/home">
                Home
              </AppSidebarItem>
              <AppSidebarItem has-children>
                Dropdown
                <template #children>
                  <AppSidebarItem to="/home">
                    Item 1
                  </AppSidebarItem>
                  <AppSidebarItem has-children>
                    Item 2
                    <template #children>
                      <AppSidebarItem to="/home">
                        Item 1
                      </AppSidebarItem>
                      <AppSidebarItem to="/home">
                        Item 2
                      </AppSidebarItem>
                      <AppSidebarItem to="/home">
                        Item 3
                      </AppSidebarItem>
                    </template>
                  </AppSidebarItem>
                  <AppSidebarItem to="/home">
                    Item 3
                  </AppSidebarItem>
                </template>
              </AppSidebarItem>
            </template>
          </AppSidebarCategory>
          <AppSidebarCategory>
            <template #title>
              Category 2
            </template>
            <template #content>
              <AppSidebarItem to="/home">
                Item 1
              </AppSidebarItem>
              <AppSidebarItem to="/home">
                Item 2
              </AppSidebarItem>
              <AppSidebarItem to="/home">
                Item 3
              </AppSidebarItem>
            </template>
          </AppSidebarCategory>
        </AppSidebar>
        <div class="transition-all duration-500">
          Content here
        </div>
      </div>
    </Variant>
    <Variant title="Minified">
      <div class="grid grid-cols-sidebar">
        <AppSidebar has-minified>
          <AppSidebarCategory>
            <template #title>
              Category 1
            </template>
            <template #content>
              <AppSidebarItem to="/home">
                Home
              </AppSidebarItem>
              <AppSidebarItem has-children>
                Dropdown
                <template #children>
                  <AppSidebarItem to="/home">
                    Item 1
                  </AppSidebarItem>
                  <AppSidebarItem has-children>
                    Item 2
                    <template #children>
                      <AppSidebarItem to="/home">
                        Item 1
                      </AppSidebarItem>
                      <AppSidebarItem to="/home">
                        Item 2
                      </AppSidebarItem>
                      <AppSidebarItem to="/home">
                        Item 3
                      </AppSidebarItem>
                    </template>
                  </AppSidebarItem>
                  <AppSidebarItem to="/home">
                    Item 3
                  </AppSidebarItem>
                </template>
              </AppSidebarItem>
            </template>
          </AppSidebarCategory>
          <AppSidebarCategory>
            <template #title>
              Category 2
            </template>
            <template #content>
              <AppSidebarItem to="/home">
                Item 1
              </AppSidebarItem>
              <AppSidebarItem to="/home">
                Item 2
              </AppSidebarItem>
              <AppSidebarItem to="/home">
                Item 3
              </AppSidebarItem>
            </template>
          </AppSidebarCategory>
        </AppSidebar>
        <div class="transition-all duration-500">
          Content here
        </div>
      </div>
    </Variant>
  </Story>
</template>
